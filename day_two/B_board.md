Explain this ruby idiom: `a ||= b`

# ParkingLot
# ParkingSpot
# HandicapStall
# CompactSpot
# Car

class ParkingLot
  attr_reader :grid
  def initialize
    @grid = Array(30) { ParkingSpot.new } 
    ...
  end
end

class ParkingSpot
  attr_reader :spot

  def initialize
    @grid_pos
    @spot
  end

  def park(car)
    @spot = car
  end
end

class HandicapStall < ParkingSpot
  
  def park(car)
    raise "You can't park here" unless car.handicap?
    super
  end
end

class Compact < ParkingSpot
  def park(car)
    raise "car too big" if car.big
  end
end

class Car
  def initialize
  end
end


class Vehicle
  attr_reader :spots_needed, :size

  def initialize(license_plate)
    @parking_spots = []
    @license_plate = license_plate
  end

  def park_in_spot(spot)
    # ...
  end

  def clear_spots
    # ...
  end

  def can_fit_in_spot(spot)
    # ...
  end
end

class Bus < Vehicle
  def initialize
    super
    @spots_needed = 5
    @size = :large
  end

  def can_fit_in_spot(spot)
    # Checks if spot is :large
  end
end

class Car < Vehicle
  def initialize
    super
    @spots_needed = 1
    @size = :compact
  end

  def can_fit_in_spot(spot)
    # Check if spot is :compact or :large
  end
end

class Motorcycle < Vehicle
  def initialize
    super
    @spots_needed = 1
    @size = :compact
  end
end

class ParkingLot
  def initialize
    @levels = # generate_levels
  end

  def park_vehicle(vehicle)
    # Park the vehicle in a spot or multiple spots. Return false if failed.
  end
end

class Level
  def initialize(floor, num_spots)
    @spots = # generate spots
    @available_spots = num_spots
    @floor = floor
  end

  def park_vehicle(vehicle)
    # Find a place to park vehicle or return false.
  end

  def park_starting_at(spot_num, vehicle)
    # Park a vehicle starting at spot number and continue until vehicle.spots_needed.
  end

  def find_available_spots(vehicle)
    # Find a spot to park the vehicle. Return index of spot or -1.
  end

  def spot_freed
    @available_spots += 1
  end
end

class ParkingSpot
  attr_reader :row, :spot_num

  def initialize(size, level, row, spot_num)
    @vehicle = nil
    @spot_size = size
    @level = level
    @row = row
    @spot_num = spot_num
  end

  def is_free?
    !@vehicle
  end

  def can_fit_vehicle?(vehicle)
    # Check it will fit.
  end

  def park(vehicle)
    # Park in spot
  end

  def unpark
    # Remove vehicle from spot and notify level that a new spot is available.
  end
end

class Node

  def dfs(&prc)
    stack = [root]
    
    until stack.empty
      checks = stack.pop

      return checks if prc.call(checks)
      stack += cheks.children
    end

    nil
  end
  
  def dfs_rec(&prc)
    
    return self if prc.call(self)

    self.children.each do |child|
      found = child.dfs_rec(&prc)
      return found unless found.nil?
    end

    nil
  end

end

## n1 = Node.new(1) #making a node with a value of 1

## n1.dfs { |node| node.value == 1 } #=> n1 (found a node with value == 1)

class Node

  def dfs(, &prc)
    raise "Must give a proc or target" if prc.nil?

    return self if prc.call(self)

    self.children.each do |node|
      result = node.dfs(target, &prc)
      return result if result
    end

    nil
  end
end

## Back to day_one

first 1 = !0, 2 = !1
factorial_arr(n)
  return [1].pick(n) if n <= 1
  arr = factorial_arr(n - 1)
  arr << (prev_facts[-1] * (n - 1))
end

digital root

def digital_root(n)
  n <= 10 ? n : digital_root((n % 10) + (n / 10))
end

def digital_root(num)
  while num > 10
    num = digital_root_step(num)
  end

  num
end

def digital_root_step(num)
  root = 0
  while num > 0
    root += (num % 10)

    num /= 10
  end

  root
end