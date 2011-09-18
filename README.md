# solid_assert

*solid_assert* is a simple implementation of an `assert` utility in Ruby. It let you code tests for your assumptions inside your code itself. 

Notice that assertions shouldn't be used for handling error situations. Use Ruby built-in exception handling for that. Assertions are meant to test conditions about the integrity of your code. You should use them for testing assumptions like the following: 

- If it reaches here, then this variable has to have this value.
- This line of code should never be executed.
- At this point, this list should contain one entry for all the keys in this hash.

The practice of using assertions makes your code more solid, since it is the computer who systematically verifies your code integrity. 

Assertions should be used in development mode. You can disable them in production for performance reasons.

# Installation

In your `Gemfile`

	gem "solid_assert"

# Usage

You can enable assertions with

	SolidAssert.enable_assertions

Assertions are disabled by default.

Use `assert` for testing conditions. You can optionally provide a message

	assert some_string != "some value"
	assert clients.list?, "Isn't the clients list empty?"
	
Use `invariant` for testing blocks of code. This comes handy when testing your assumptions requires several lines of code. You can provide an optional message if you want

	invariant do
		one_variable = calculate_some_value
		other_variable = calculate_some_other_value
		one_variable > other_variable
	end

	invariant "Have the lists had different sizes?" do
		one_variable = calculate_some_value
		other_variable = calculate_some_other_value
		one_variable > other_variable
	end

## References

- [Programming with assertions](http://download.oracle.com/javase/1.4.2/docs/guide/lang/assert.html). A great article on assertions. It is about the Java language, but the concepts it explains apply to any programming language.
- [Writing Solid Code](http://www.amazon.com/Writing-Solid-Code-Microsoft-Programming/dp/1556155514). A great book on good coding design practices. Again, it is related to C, but the practices it talks about apply to coding in any programming language.



