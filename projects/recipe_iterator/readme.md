# Recipe Iterator
## *Or:* You do stuff, you handsome chef, you, and we'll remember what you did — and later, should the occasion arise —  remind you if it was a good idea or not 

Ahem. 

To understand the `problem` this project attempts to resolve, it is unfortunately first necessary to understand a bit of `background`.

### ——Background:
* **Good**: I am addicted to milk tea
* **Bad**: I have osteoporosis
* **Double bad**: Tea has caffeine, which weakens your bones, and mine are already porous
* **Triple bad**: Deccaffeinated tea lacks the kick necessary to make a respectable mug of milk tea

Thus, while I have lost about 50 years of bone health, I have in turn been bestowed with a most noble quest: to produce a palatable pot of decaffeinated milk tea. 

### ——Problem:
I have made over 300 variations upon [ye old tea (with milk)](https://www.youtube.com/watch?v=xqXTJlU3NTQ). 

Optimistically speaking, they've all sucked. 

Thus far, I have kept my experiments in a little notebook:
1. I make a cup of tea each day
2. I list my ingredients, sequence of ingredients, boil times, and such
3. I score it
4. The next day I tweak the recipe accordingly
5. <details>
    <summary>Sample recipe</summary>
    </br>
    This is the recipe I am most satisfied with so far:
    
    - 2/3 cup water
    - Spices (add after boiling)
      - 1/2 knuckle ginger
      - 1 knuckle cinnamon 
      - 1/2 tsp cardamom powder 
      - 1/4 tsp black pepper 
      - 1/4 tsp corriander powder
    - Boil 7 minutes / water level should noticeably drop 
    - Then
      - Add 1/2 tsp sugar 
      - Add 2 tea bags (decaf yorkshire)
      - Boil 3 min more  
    - add 1 MyCup (300ml) milk
      - Reduce heat to low-med
      - Slowly bring to boil
      - Add 1 dinner spoon honey, stir in
      - Bring to simmer, remove from heat ... repeat 3x
    - Strain 2x
    - Pull tea 8x
  </details>


I have recently found myself with two problems, one very much expected and the other somewhat of a surprise:
* British-style "tea with milk" sucks
* I spend more time referencing my notebook to confirm that I have/have not tried {recipe} than I actually do making tea

I would like to make a tool to solve both of these problems. 

### ——Project / proposed solution

The Recipe Iterator! Version control for cooking. 

* Separate recipes will be stored as .csv's (British tea with milk, Indian masala chai, Taiwanese boba tea, Somali Shaah Cadays, etc)
* Potential .csv structure: tea type, iteration #, recipe([ingredient + amount], [action + (temp + time) _or_ (count)]), score/100, comment
* The first file version is `iteration 1`
* Each new iteration wil create a new database entry, `iteration += 1`
* Examples of things ot be included in `recipe()`
  * Ingredients
  * Sequence of ingredients
  * Amount of each ingredient
  * Boils (time and temperature)
  * etc

* Each time you iterate upon the recipe, it will compare `current iteration` with all `past iterations` to make note of and compare things like `sequence` and `ingredient_ratios`
  * `Sequence` example: in Somali-style tea, milk is the base and immediately boiled; in British-style tea, you start by boiling water, and then add in milk only at the end
  * `ingredient_ratios` example: water 300ml:milk 200ml
* A user will input any observations they make, for example:
  * `ingredient_ratio.milk:water`: The tea is too weak. 3:2 water:milk is too milky. 

### ——Expected / desired result

If succesful, this will result in an ever-improving database of your preferences. 

The idea is that I can make `[tea] iteration 27` and comment `ingredient_ratio.milk2:water3: too watery`. The tool will remember my feedback. In the future, if I input the same `milk:water` ratio, it will display a note: `Previously, you indicated that the "ingredient_ratio" "milk:water" resulted in "too watery". Consider [using/changing] this "ingredient_ratio"`. (where [using] is chosen if `score > 70`, [changing] if `score < 70`)

This will also "tree" or "fork" recipes, so that comments made for `british.sun_tea` will not apply to `british.fresh_tea`... but it _will_ reference `sequence` or `ingredients` to inform me that `average score for "britsh.sun_tea" is #points [higher/lower] thahn "british.fresh_tea"`. 

The goal is that I can completely forget about what iterations of a recipe I have done in the past. I can simply do whatever is on my mind now, using whatever is at hand now, and the tool will inform me if any of this iterations `values` match a previous iteration's `values` and return any comments previously made about those `values`. I can thus reproduce a result deemed desirable or avoid a result deemde undesirable.

If this works as expected, the tool will keep track of all the knowledge gained upon my tea making journey until I have eventually found the perfect recipe. 

### ——Desired feedback:

The sum of my programming experience is the first 8 chapters of Boot.dev and about 15 hours goofing around with SQL. I don't really have any idea how difficult this would be, what technologies I would need, or how to get started.

Anything that jumps out at you is welcome!

