# AR_MongoDB
Active Record with mongo db

# Configuration

Rename `config.rb.example` of dir config to `config.rb`  
change data by your informations.

# Create new model

When you create a new model of your mongo collection, you have to create a class
with inheritance to `DBElement` or `DBArray`

## DBArray
_contains mulptiple dbElements (array)_

To define elements in array you have to add to initialize the next line `@contentClass=yourClass`

Example:
```ruby
class SequenceArray < DBArray
    def initialize
        @contentClass=Sequence
    end
end
```

## DBElement
_is a specific element of mongo collection_

All class inheritance DBELement have an hash with the next name `@attributes`.
If you want a specific collection you have to add the class of your collection (example, if you want player
collection you have to write Player).
Else you use fundamentals information (String, integer ...).

Example : 
```ruby
class Level < DBElement
    def initialize
        @collection_name = "levels"
        @attributes = {
            id: String,
            name: String,
            difficulty: String,
            hardcore: Integer,
            music: Music,
            sequence: Sequence,
            texture: Texture,
            creator: Player
        }
        super
    end
end
```

# Informations
You can use `to_hash` to transform your object in hash or `to_json`to convert object in json information.
If your object return an array, you can use `array_to_hash` to get an hash.

This library only work with **mongoDB**.
