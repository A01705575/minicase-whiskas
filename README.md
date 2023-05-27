# Mini case 1 - Linear programming
Emiliano Bañuelos Rojas  | A01705575

Alan Ortiz de Zárate Soto Borja | A01735680

Karyme Pérez Chatú | A01174367

Kevin Manuel Gámez Garzón | A01640443


May 27th, 2023
# 1. What are the two parameters that the LpProblem function implements?
In this case the two decision variables implemented in the objective function are “ChickenPercent” and “BeefPercent”, this in consideration of the WhiskasModel1.py which is a simplified formulation of the Whiskas case.
# 2. Is it mandatory to name the prob variable as prob?
It’s not an obligatory naming convention, as long as it serves the same purpose of being the problem variable name and it’s used throughout the code. What you can’t do is try to add a space inside the variable, it won’t work, if such a word separator is needed you use a hyphen (-) or an underscore ( _ ).
# 3. What are LpContinuous and LpInteger used for?
Basically LpInteger is used when we’re working with discrete data which is defined by having a limited numbers of possible values, it’s used for values that don’t have a fractional component while LpContinuous, as its name implies, works with continuous data which encompasses complex data and varying data values measured over  a particular time interval. In the Whiskas simplified model the optimal result gives us “BeefPercent = 66.666667” and “ChickenPercent = 33.333333” if we were to use LpContinuous while using LpInteger gives us “BeefPercent = 66.0” and “ChickenPercent = 34.0”, a far more concise answer.
# 4. Explain and copy the section of code that defines the objective function.
#The objective function is added to 'prob' first

prob += 0.013 * x1 + 0.008 * x2, "Total Cost of Ingredients per can"

As we can see we’re defining each of the variable’s cost, the cost of ingredient for the chicken percentage of the can is $0.013 and $0.008 for the beef and as such in this simplified model the sum of both make for the total cost of ingredients. The objective function in this case has “LpMinimize” so the function we’re actually doing would be min0.013x1 + 0.008x2.
# 5. Explain and copy the section of code that defines the constraints.
#The five constraints are entered

prob += x1 + x2 == 100, "PercentagesSum"

prob += 0.100 * x1 + 0.200 * x2 >= 8.0, "ProteinRequirement"

prob += 0.080 * x1 + 0.100 * x2 >= 6.0, "FatRequirement"

prob += 0.001 * x1 + 0.005 * x2 <= 2.0, "FibreRequirement"

prob += 0.002 * x1 + 0.005 * x2 <= 0.4, "SaltRequirement"

These are the limitations/restrictions for the decision variables of “ChickenPercent” and “BeefPercent” presented in code. We take this from the Whiskas ingredients contribution table (in grams) which basically works as  the Nutrition Information/Facts label for the can which breaks down the amount of protein, fat, fibre and salt of each ingredient. The constraint is that they must amount to the 100-grams Whiskas Senior Cat Food can. We get the 8.0, 6,0, 2.0, and 0.4 (and their respective symbols) from the following statement: “To meet the nutritional analysis requirements we need to have at least (≥) 8g of Protein per 100g, 6g of fat, but no more than (≤) 2g fibre and 0.4g of salt”.
# 6. Is this a minimization or maximization problem?
It’s a minimization problem for both the simplified and full model, why? Well, we’re trying to optimize the total costs of ingredients per can which should be at its cheapest/minimum value cost of production, maximizing here would mean finding the maximum value of the same objective function or a higher cost. Maximization is far more useful when we want to know the maximum profit we can achieve with whichever quantity of cans but that’s not what the exercise is asking for.
# 7. Run the WhiskasModel1.py code. (no need to make changes, just run it as is) What is the value of the following variables? Status: BeefPercent = ChickenPercent = Total Cost of Ingredients per can =
Status: Optimal

BeefPercent = 66.0

ChickenPercent = 34.0

Total Cost of Ingredients per can =  0.97
