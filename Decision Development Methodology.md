# Rule Development Methodology

## Identify the decision being made.
For example “Determine the overall insurance risk for a property along with its annual premium”
A *decision* is *one or more rules* that may be organised into a number of *rule groups*

## Identify the factors that affect the decision. 
For example:
*	Insurance risk pricing tier is based on three factors: The customer risk, the property risk and the coverage risk.
*	Customer risk is based on customer bankruptcies, years at current address and years in business.
*	Property risk is based on type of construction, age, value and prior losses
*	Coverage risk is based on the type of peril and the coverage required

These factors might end up being sub-decisions in their own right.

## List in English the rule statements that make the decision 
Example:
Customer Rules
*	Customers with more than one bankruptcy are poor risk
*	Customers with one bankruptcy who have been in business for less than 5 years and have lived at their current address for less than 5 years are poor risk
*	Customers with one bankruptcy but more than 5 years in business or at current address are average risk
*	Customers with no bankruptcies are considered excellent risk
Property Rules
Coverage Rules

## Identify the business objects, attributes and data types of these factors.

### Customer has 
*	number of bankruptcies (which might be retrieved from a credit report), 
*	years in business and
*	 years at current address (as reported on the application form)
### Property has
*	has type of construction (Brick, Sticks, Straw), 
*	year of construction (from which age is determined), 
*	value (based on latest Zillow reports) and
*	 total amount of prior claimed losses (either reported by new customers or obtained from the database for existing customers)
### Coverage has
*	Type of  peril (wolf attack, wind)
*	Type of coverage (medical, content)

## Develop a formal vocabulary that defines the business objects, factors, attributes and types
This could be done with a UML diagram

## Define the relationships between the various business objects
Customers can have one or more properties. Properties can have one or more coverage. 
If these already exist in a database (or other data source) you may be able to automatically generate the vocabulary

## Identify the sequence of steps involved in making the decision
 This may be defined in the ruleflow diagram. 
 If an inference engine is being used then it may automatically determine the order of execution based on the goal and the various dependencies 

## Group the rules into rule groups. 
Typically all the rules that set the value of a given attribute will be in the same rule group. 
This is to ensure that you can do proper completeness and ambiguity checks. 
Sometimes the rules may be in multiple rule groups that are mutually exclusive. 
To ensure conflict free rules these should be set up in a branching rule flow.

## Enter all of the English rule statements that apply to each rule group. 
Initially these will be plain English statements. 
Later you may find it helpful to supplement these with actual values that occur during execution. 
If the source of the rules is actual code then you can also copy that into the rule statements as a reference.

## Enter the natural language for each condition and action in the rule statement 
You don’t need any special syntax here – 
the important thing is to capture the intent of the rule regardless of what data or attributes might later be used to implement it.

## Enter an expression that implements each of the natural language statements
There are usually many different ways to implement a particular business intent. 
Ideally try to fnd an implementation that mirrors the structure of the English rule statement.

## Check the rules for ambiguity
Fix any ambiguities by making the rules more specific. Avoid the temptation to use the override mechanism – 
it’s just too hard to see what’s happening if you do that.

## Check the rules for completeness. 
Add any required missing rules. 
Even if you don’t care about those cases sometimes it’s helpful for the rules to explicitly say so just to avoid any misunderstanding. 
You may find that the completeness checker adds a lot of extra rules to deal with null values. 
You can either deal with them in the rule group if there aren’t too many. 
But a better approach is to create a validation rule group at the beginning of the decision that ensures that all required data is present. 
If it’s not then there’s no point in trying to execute the rest of the rules. 
If null is a valid value that the rules need to deal with then handle that in the rule group that deals with it.

## Create a test group for each rule group on its own.
 If you make sure that each rule group is giving the proper results on its own you will have less headaches when you start putting them together in a ruleflow. 

## Create a test case for every rule in your rule group. 
That’s the only way you can be sure it’s fully tested. You can usually do this by entering multiple test entities in a single test tab. 
Sometimes you need multiple tabs. For example to test the case where there is no input at all.

## Once rule groups are created and tested you can start assembling them into rule flows. 
You could just string all the rule groups into one very long flow. 
But in general it’s better to group related rule groups. 
You can do this in a single rule flow by using subflows or functions. 
Or if there are a lot of rule groups it can be more manageable to create separate ruleflows and then include them on the master flow that represents the decision service. 
You can always drill down from the top level ruleflow into the lower level ones.
It can be helpful to color code the various element of a ruleflow to aid in understanding

## Create test cases for the entire rule flow. 
If you have already thoroughly tested the individual rule groups this step should be fairly easy. 
At this point you are more concerned with the interaction of the rule sheets than their individual behavior.
If the ruleflow is particularly complex it can be helpful to develop additional rule groups whose purpose is to provide a cross check on the other rule groups. 
One example of this is a rulesheet that cross checks totals of records processed. 
Another example is rule groups that check to make sure that all rules have been tested by at least one test case.
