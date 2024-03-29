# Restaurantes
Crear una WebApp que consulte los restaurantes de Estados Unidos

class Restaurant
  COUNTRIES = %w(AE AW CA CH CN CR GP HK KN KY MC MO MX MY PT SA SG SV US VI)
  
  include Mongoid::Document
  include Mongoid::Timestamps
  include Mongoid::Pagination

  field :restaurant_id, type: Integer
  field :name
  field :address
  field :city
  field :state
  field :postal_code
  field :metro_name
  field :phone
  field :country
  field :latitude,  type: Float
  field :longitude, type: Float
  field :location,  type: Array
  field :price, type: Integer

  validates :restaurant_id, presence: true, uniqueness: true
  validates :name,          presence: true

  index restaurant_id: 1
  index city: 1
  index state: 1
  index postal_code: 1

  def as_json(options = {})
    RestaurantSerializer.new(self, options).to_hash
  end

  def self.valid_country?(code)
    COUNTRIES.include?(code)
  end

  def self.unique_countries
    Restaurant.collection.distinct("country").compact.sort
  end

  def self.unique_cities
    Restaurant.collection.distinct("city").compact.sort
  end

  def self.by_id(id)
    Restaurant.where(restaurant_id: id).first
  end

  def self.import_records(results)
    results.each_slice(100) do |batch|
      collection.insert(batch)
    end
  end
end
