# Alex Rizk
# This program will be a budget and expenses calculator. It will calculate
# (continued) common expenses and bills that one would have in a month.
#It will also calcultate how much you make and determine if you have excess
# (continued)money or not. Then it will tell you your tax bracket.
#The next couple lines will just assign variables to something that you input,
# (countinuedthen add up all the varaibles and print it.

print("Hello. Welcome to the Expenses Calculator")
input("Press enter to continue")
def expenses(mortgage_or_rent, house_insurance, electric, utilities,
             car_payment, car_insurance, gas, phone, food, entertainment,
             clothing, savings):
    expenses_total = (mortgage_or_rent + house_insurance + electric + utilities
                      + car_payment + car_insurance + gas + phone + food +
                      entertainment + clothing + savings)
    total = expenses_total
    return total
def main():
    mortgage_or_rent = float(input("Enter the cost of your mortgage/rent for "
                                   "the month: $"))
    house_insurance = float(input("Enter the cost of your house insurance for "
                                  "the month: $"))
    electric = float(input("Enter the cost of your electric bill for the month:"
                           " $"))
    utilities = float(input("Enter the cost of your utility bill for the "
                            "month: $"))
    car_payment = float(input("Enter the cost of your car payment for the "
                              "month: $"))
    car_insurance = float(input("Enter the cost of your car insurance for the "
                                "month: $"))
    gas = float(input("Estimate the amount you spend for gas in a month: $"))
    phone = float(input("Enter the cost of your phone and/or cell phone bill "
                        "for the month: $"))
    food = float(input("Enter the cost you spend on food/groceries for the "
                       "month: $"))
    entertainment = float(input("Enter the cost spent on entertainment for "
                                "the month: $"))
    clothing = float(input("Enter the amount you spend for clothing for the "
                           "month: $"))
    savings = float(input("Enter the amount you set aside for savings for the "
                          "month: $"))
    expenses_total = expenses(mortgage_or_rent, house_insurance, electric,
                              utilities, car_payment, car_insurance, gas,
                              phone, food, entertainment, clothing, savings)
    print("Total expenses for the month: $"+ format(expenses_total, '.2f'))
    # formats total for 2 deciamal places
main()
#The next lines of code will now calculate the amount of money you make.
salaried_or_wage = None
while salaried_or_wage not in ("salaried", "wage"):
# the 2 previous lines of code i got the idea from Martin O'Shea, Sept 20,
# 2017, https://www.quora.com/I%E2%80%99m-new-to-Python-how-can-I-write-a-yes-
# no-question
# It creates a loop that keeps asking the question if you dont give the right
# answer
    salaried_or_wage = input("Are you a salaried employee or wage employee? "
                             "Enter salaried or wage. ")
    if salaried_or_wage == ("salaried"):
        #The next lines calculate your net monthly salary, taking taxes out of
        # your gross salary
        gross_annual_salary = float(input("Enter your gross annual salary: "))
        gross_monthly_salary = (gross_annual_salary / 12)
        taxes = (gross_monthly_salary * 0.1029)
        # 10.29% federal income tax, no state tax in florida
        social_security = (gross_monthly_salary * 0.0620)
        # 6.20% taken out of social security
        medicare = (gross_monthly_salary * 0.0145)
        # 1.45% taken out for medicare
        net_monthly_salary = (gross_monthly_salary - taxes - social_security
                              - medicare)
        net_weekly_salary = (net_monthly_salary // 4)
        print("Your net monthly income is $"+ format(net_monthly_salary,
                                                     '.2f'))
        #The next lines apply to wage workers. You will get this option if you
        # answer "wage" on the question "Are you a salaried employee or wage
        # employee?" above.
    elif salaried_or_wage == ("wage"):
        hours = int(input("How many hours do you work a day? "))
        days = int(input("How many days do you work per week? "))
        pay = float(input("How much do you earn per hour worked? "))
        gross_weekly_pay = (hours * days * pay)
        taxes = (gross_weekly_pay * 0.1029)
        social_security = (gross_weekly_pay * 0.248997992**2)
        medicare = (gross_weekly_pay * 0.0145)
        net_weekly_pay = (gross_weekly_pay - taxes - social_security -
                          medicare)
        net_monthly_pay = (net_weekly_pay * 4)
        net_weekly_pay =(net_monthly_pay % 4)
        print("Your net monthly income is $"+ format(net_monthly_pay, '.2f'))
    else:
        print("Enter salaried or wage: ")
input("Press enter to continue")
input("Now lets find out if you earn enough to cover your expenses. Press "
      "enter.")
from expenses import expenses_total
if salaried_or_wage == ("salaried"): # if you picked salaried earlier, your
    # leftover money will be calulated here.
    leftover = (net_monthly_salary - expenses_total)
    print("You have $"+ format(leftover, '.2f'))
    if leftover < 0 and leftover != 0: # If your amount is negative this is
        # not good. So the program will tell you.
        print("You need to manage your budget better.")
    else:
        print("Good job! You have leftover.")
elif salaried_or_wage == ("wage"): # if you picked wage earlier, your leftover
    # money will be calulated here.
    leftover2 = (net_monthly_pay - expenses_total)
    print("You have $"+ format(leftover2, '.2f'))
    if leftover2 <=0 or leftover2 !=0:
        print("You need to manage your budget better.")
    else:
        print("Good job! You have leftover.")
input("Press enter to continue")
five_year_income = 5
for x in range(1): #Only works for one entry
    filing = None
    while filing not in ("single", "joint", "hoh"): #loop that is used if the
        # user does not enter the correct input. It will re ask the question
        filing = input("Are you filing your tax as single, joint(married), or"
                       " head of household? Enter, single, joint or hoh. ")
        #The outcome depends on how you file you tax as
        income = int(input("Enter your income: $")) #Annual income
        if filing == ("single"): #for single filers
            if income >= 518401:
                print("You're in the 37% bracket.")
            elif income >= 207351 and income <= 518400:
                print("You're in the 35% bracket.")
            elif income >= 163301 and income <= 207350:
                print("You're in the 32% bracket.")
            elif income >= 85526 and income <= 163300:
                print("You're in the 24% bracket.")
            elif income >= 40126 and income <= 85525:
                print("You're in the 22% bracket.")
            elif income >= 9876 and income <= 40125:
                print("You're in the 12% bracket.")
            else:
                print("Your in the 10% bracket.")
        #All the numbers are the tax brackets depending on how much you make
        elif filing == ("joint"): #for joint filers
            if income >= 622051:
                print("You're in the 37% bracket.")
            elif income >= 414701 and income <= 622050:
                print("You're in the 35% bracket.")
            elif income >= 326601 and income <= 414700:
                print("You're in the 32% bracket.")
            elif income >= 171051 and income <= 326600:
                print("You're in the 24% bracket.")
            elif income >= 80251 and income <= 171050:
                print("You're in the 22% bracket.")
            elif income >= 19751 and income <= 80250:
                print("You're in the 12% bracket.")
            else:
                print("Your in the 10% bracket.")
        elif filing == ("hoh"): #for head of household filers
            if income >= 518401:
                print("You're in the 37% bracket.")
            elif income >= 207351 and income <= 518400:
                print("You're in the 35% bracket.")
            elif income >= 163301 and income <= 207350:
                print("You're in the 32% bracket.")
            elif income >= 85501 and income <= 163300:
                print("You're in the 24% bracket.")
            elif income >= 53701 and income <= 85500:
                print("You're in the 22% bracket.")
            elif income >= 14101 and income <= 53700:
                print("You're in the 12% bracket.")
            else:
                print("Your in the 10% bracket.")
        else:
            print("Enter, single, joint or hoh." * 3)
five_year_income *= income
#shortcut operator takes the variable which is equal to 5, and multiplies
# (continued) itself by the income, to get your 5 year income
print("The amount you make in 5 years excluding taxes is $",five_year_income)
