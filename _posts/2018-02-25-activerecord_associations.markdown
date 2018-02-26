---
layout: post
title:      "ActiveRecord Associations"
date:       2018-02-26 00:18:00 +0000
permalink:  activerecord_associations
---



When writing a simple Ruby program we create associations by hand.


Say we are writing a video game that has characters and they own objects and they belong to a group that is questing merrily along attempting to save the town from a band of marauding goblins.

The Dungeon class would have instances of each Enemy class (ie goblins, wolves, etc.) and each of those Enemy Objects would have equipment and loot. Equipment and loot would also be objects of a class(s) Treasure or Equipment. We haven't even touched the adventure group who would have equipment and treasure as well as quests, levels, skills, and so on. It gets messy <em>fast</em>. As programmers we don't like messy. It makes it difficult to debug and refactor.


Databases make this so much easier and when using Ruby we use ActiveRecord which automates all of that manual object associating.

There are many different types of associations:

<ul>
<li>belongs_to</li>
<li>has_one</li>
<li>has_many</li>
<li>has_many :through</li>
<li>has_one :through</li>
<li>has_and_belongs_to_many</li>
</ul>


Instead of manually writing out each of the associations these macros makes it so you don't have to micromanage and it adds a lot of different methods that you don't have to write them out. Most importantly it associates the objects by assigning their primary and foreign ids automatically for us and also automatically dessociates them when we destroy the object. 

I'm going to go over how the id's are assigned for the more common associations.

Lets say a character has an individual character quest.
```
class Quest

belongs_to :character

end
```

One method it inherits is:

```
character=
```

This associates the Quest and Character classes so that** Quest has a foreign id of character_id.** Therefore, this instance of Quest belongs *to only this instance* of Character.

Though a Quest can belong to one character say your character has many health potions to keep them alive on their adventure.

```
class Character

has_many :potions

end

```

This creates an association where **each potion has a foreign id of character_id** which associates that potion with that character.

```
character.potions
character.potion_ids
```
Allows you to see an array of potions that the character owns and allows the programmer to use the potions array as they would any other array of objects. It also gives you the potion_ids method which is an array of the primary keys of the potions.

Now to make things more complicated, say that you have a group of adventures and they go on a quest where they acquiretreasure. Not any individual character owns all the treasure and therefore the treasure also belong to the whole group (not just an individual).

We end up with the has_and_belongs_to_many association.

```
class Treasure

has_and_belongs_to_many :characters

end
```

Though this will probably work has_and_belongs_to_many is deprecated so it is better to use the has_many :through association and using a join model which would be represented as is shown below.

```
class CharacterTreasure

belongs_to :character
belongs_to :treasure

end


class Treasure

has_many :character_treasures
has_many :characters, through: character_treasures

end


class Character

has_many :character_treasures
has_many :treasures, through: character_treasures

end
```

The database for the CharacterTreasure model has a foreign id for both the Treasure and the Character models and associates them <em>through</em> the join table and both the Character and Treasure models get the treasure_ids and character_ids arrays respectively making it easy to iterate through the different associated objects.

<a href='http://roseweixel.github.io/images/revised_character_actor_with_join.png'>Here</a> is a good visual representation of the tables in a has_many through  relationship.

There are many more methods that are given through ActiveRecord. I recommend checking out the Rails guide on <a href='http://guides.rubyonrails.org/association_basics.html#choosing-between-has-many-through-and-has-and-belongs-to-many'>ActiveRecord Associations</a> and the <a href='http://api.rubyonrails.org/classes/ActiveRecord/Associations/ClassMethods.html'>class methods</a> documentation.













