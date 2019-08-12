class Juckbox

    def intialize
    end

    def store_music
    end

    def show_buttons
    end

    def select_music
    end

    def play_music
    end
end

class Music

    def initiailize
    end

    def selection
    end

    def display_selection
    end

    def retreive_selection
    end

    def play_selection
    end
end

class Buttons

    def initalize
    end

    def select
    end

    def display
    end

    def button_actions
    end
end

class Jukebox
 attr_accessor :user
  attr_reader :current_track

  def initialize(player, user)
    @player = player
    @user = user
    @current_track = nil
  end
end

class Player
  attr_accessor :album, :playlist

  def initialize(album, playlist)
    @album = album
    @playlist = playlist
  end

  def play_track(track)
    # Begin playing...
  end
end

class Playlist
  def initialize
    @queue = []
  end

  def add_track(track)
    @queue.push(track)
  end

  def shift
    @queue.shift
  end
end

class Album
  # Information about the album
end

class Track
  # Information about the track, including album
end

class User
  # Information about the user.
end


class Node 

    def bfs(target, &prc)
        queue = [root_node]

        until queue.empty?
            dequeue = queue.shift
            if prc.call(dequeue)
                return dequeue
            else
                queue.push(*dequeue.children)
            end
        end
        nil
    end
end

class Node

  # -- Assume nodes have a value, and a attr_reader on value
  # -- Also, assume there are working parent/child-related methods for Node

  def bfs(target, &prc)
    raise "Must give a proc or target" if prc.nil?
    
    #prc ||= { |v| v == target } (prc.new { target })

    queue = [self]

    until queue.empty?
      visited = queue.shift
      return visited if prc.call(visited)
      queue += visited.children
    end

    nil
  end
end


## Back to day_one 

# adds each element one by one. my-inject
# block, accumulator

class Array

    def reduce(accumulator = nil, &prc)
        arr = self.dup
        if accumulator.nil?
            accumulator = arr.fist
            arr = arr[1..-1]
        end

        arr.each do |ele|
            prc.call(accumulator, ele)
        end

        self
    end
end

{ |ele| acc += ele.idx }

class Array
  def my_reduce(accumulator = nil, &block)
    i = 0
    if accumulator.nil?
      accumulator = self.first
      i += 1
    end

    while i < length
      accumulator = block.call(accumulator, self[i])
      i += 1
    end
    accumulator
  end
end

shuffled sentances
```ruby
"cats are cool".shuffled_sentence_detector("dogs are cool") => false
"cool cats are".shuffled_sentence_detector("cats are cool") => true
```
class String

    def shuffled_sentence_detector(sentance)
        word_count = Hash.new(0)

        self.split.each { |word| word_count[word] += 1 }
        sentance.split.each { |word| word_count[word] += 1 }

        word_count.values.all?(&:even?)
    end
end

class String
  def shuffled_sentence_detector(other)
    self.split.sort == other.split.sort
  end
end
