# Boolean Expressions

## Learning Goals

* Use Equality Comparison
* Use Inequality Comparison
* Use Greater-Than Comparison `>`
* Use Less-Than Comparison `<`
* Use Greater-Than-or-Equal-To Comparison `>=`
* Use Less-Than-or-Equal-To Comparison `<=`
* Invert Truth Value with "Bang" (`!`)
* Invert Truth Value with "Double-Bang" (`!`)
* Identify Truthy and Falsey Values in Python
* Join Boolean Expressions with AND
* Join Boolean Expressions with OR

## Introduction

As we saw in the ternary expression, sometimes we need to get a Boolean value
(`True` or `False`) _from_ an expression in order to use it _in_ another
expression.  We showed that we can use greater than (`>`) and less than (`<`)
to perform comparisons that produce `True` or `False`. Let's learn more!

## Arithmetic Comparisons

### Use Equality Comparison

To check whether two values are equal, we use the *equality operator* represented
with `==` ("double-equal-sign"). If two values are equal, then the statement
will return `True`. If they are not equal, then it will return `False`. For
example:

```Python
1 == 1 #=> True

1 == 7 #=> False
```

**IMPORTANT**: *The comparison operator* `==` *is distinct from the assignment
operator*, `=`, *that is used to set a variable equal to a value. Mistaking these
for each other is a common cause of unexpected behavior.*

Now, this might feel a bit weird, because you're used to thinking about `=` only
being around numbers like `Integer` and `Float`. But you can also compare
`String`s:

```Python
"Razz" == "Matazz" #=> False

"Poodle" == "Poodle" #=> True

"Poodle" == "poodle" #=> False
```

### Use Inequality Comparison

To check whether two values **are not** equal, we use the *inequality operator*
represented with `!=` ("bang-equal-sign;" more on "bang" below). If two values
are not equal, then the statement will return `True`. If they are equal, then
it will return `False`. For example:

```Python
1 != 1 #=> False

1 != 7 #=> True

"Poodle" != "Lord of the Manor" #=> True
```

## Quantity Comparisons

You might recall these from middle-school: comparisons of greater-than /
greater-than-or-equal-to.

### Use Greater-Than Comparison `>`

If the value on the left of the operator is *greater than* the value on the
right, then the evaluation is `True`; `False` otherwise.

### Use Less-Than Comparison `<`

If the value on the left of the operator is *less than* the value on the
right, then the evaluation is `True`; `False` otherwise.

### Use Greater-Than-or-Equal-To Comparison `>=`

If the value on the left of the operator is *greater than or equal to* the
value on the right, then the evaluation is `True`; `False` otherwise.

### Use Less-Than-or-Equal-To Comparison `<=`

If the value on the left of the operator is *less than or equal to* the
value on the right, then the evaluation is `True`; `False` otherwise.

## Invert Truth Value with `not`

The `not` keyword inverts a truth value. Here's the most simple version:

```Python
not True #=> False
not False #=> True
```

We can also invert the truth value of an expression:

```Python
( 1 + 1 == 2 ) #=> True
not ( 1 + 1 == 2 ) #=> False
```

Since `1 + 1` evaluates to `2`; and since `2 == 2` the return value is `True`.

## Invert Truth Value Twice with `not not`

Using `not not` inverts a truth value _twice_. Here's the most simple version:

```Python
not not True #=> True
not not False #=> False
```

We can also do this to an expression:

```Python
not not ( 1 + 1 == 2 ) #=> True
```

Now why would this ever be useful? Great question. It turns out Python will treat
a whole bunch of values as `True` that aren't the literal `True`. We call those
values "truthy." Similarly, there are values that, even if they aren't the
literal `False`, Python treats as false. We call those values "falsey."

This next statement is very important:

> **IMPORTANT**: Python will treat anything that is `False`, `0` or `None` as
falsey

So:

```Python
True if False else False  #=> False
True if 0 else False  #=> False
True if None else False  #=> False
True if 6.7 else False  #=> True
True if 1 + 1 else False  #=> True
True if "hello" else False #=> True
```

In each of the examples above, we wanted to return whether the `truthy` or
`falsey` value was a real-deal `True` or `False`. What a lot of code to type.
But here's where our friend `not not` comes in:

```Python
not not False #=> False
not not 0   #=> False
not not None #=> False
not not 6.7   #=> True
not not 1 + 1 #=> True
not not "hello" #=> True
```

Programmers often use `not not` to show other programmers "Hey, I'm being clever
here and am using a truthy (or falsey) value.

## Identify Truthy and Falsey Values in Python

This concept is ***so*** important we're going to repeat it again here:

> **IMPORTANT**: Python will treat anything that is `False`, `0` or `None` as
falsey

## Join Boolean Expressions with AND

In Python `and` is used to join two Boolean expressions, returning `True` or
`False`. For an `and` to evaluate to `True`, both values of either side of `and`
must evaluate to `True`. For example:

```Python
True and True #=> True

True and False #=> False
```

It's common to say things like:

IF it's Thursday AND my Mom is not home THEN I will play scary video games all
night on the living room TV.

In Python we would express this "double-conditional" like so.

```Python
day_is_thursday = True
mom_is_not_home = True

# Ternary
# Position 1                # Position 2                             # Position 3
"play scary video games" if day_is_thursday and mom_is_not_home else "do homework"
```

## Join Boolean Expressions with OR

In Python `or` is also used to join two Boolean expressions. For an `or` to
evaluate to `True`, only one value on either side of `or` must evaluate to
`True`. For example:

```Python
False or True #=> True
```

Of course, keep in mind, these Boolean values can, themselves, be Boolean
expressions!  Instead of `False and True` it could be another expression that
results in `True` or `False` like `(poodle_count > 12) and (owner == "Lorlei
Gilmore")`

## Longer Expressions

Because of the ability to use `()` and `and` and `or`, we can create
surprisingly rich programs:

```Python
chance_of_precipitation = 1000
temperature = -1000
it_is_wet = ( chance_of_precipitation > 0.5 )
it_is_cold = ( temperature <= 5 )
"snow-suit" if it_is_wet and it_is_cold else "something less bulky" #=> "snow-suit"
"umbrella" if it_is_wet and not it_is_cold else "light fabric" #=> "light fabric"
```

Try changing some of the values or expressions to make sure you understand how
to _express_ your ideas using variables and Boolean conjunctions!

## Conclusion

While it might seem strange that these simple little conditional expressions are
so tiny, stacked together, they can have a big impact!

Most social media sites have a bit of conditional logic **just like this one**.

```Python
top_corner_image = retrieve_profile_pic if (user_logged_in and profile_pic_uploaded) else default_avatar
```

With this collection of comparison operators you're able to express a
surprisingly complex series of desires to Python! Your programming conversational
level is nearing the pre-teen stage!
