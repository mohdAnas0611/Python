# Python
def calculate_bmi(weight, height):
    return (weight * 703) / (height * height)

def determine_bmi_category(bmi):
    if bmi < 18.5:
        return "underweight"
    elif bmi <= 24.9:
        return "normal weight"
    elif bmi < 29.9:
        return "overweight"
    elif bmi < 34.9:
        return "obese"
    elif bmi < 39.9:
        return "severely obese"
    else:
        return "morbidly obese"

def get_user_input():
    name = input("Enter your name: ")
    weight = float(input("Enter your weight in pounds: "))
    height = float(input("Enter your height in inches: "))
    return name, weight, height

def display_results(name, bmi, category):
    print(f"\n{name}, your BMI is: {bmi:.2f}")
    print(f"You are classified as: {category}")

def main():
    print("Welcome to the BMI Calculator!")
    
    name, weight, height = get_user_input()
    
    bmi = calculate_bmi(weight, height)
    
    category = determine_bmi_category(bmi)
    
    display_results(name, bmi, category)

    if category == "underweight":
        print("Advice: Consider consulting a healthcare provider for guidance on healthy weight gain.")
    elif category == "normal weight":
        print("Advice: Maintain your current lifestyle for optimal health.")
    elif category == "overweight":
        print("Advice: Incorporate regular exercise and a balanced diet into your routine.")
    elif category == "obese":
        print("Advice: It's advisable to seek guidance from a healthcare professional for weight management.")
    elif category == "severely obese":
        print("Advice: Consult a healthcare provider for a personalized weight loss plan.")
    elif category == "morbidly obese":
        print("Advice: Immediate medical intervention may be necessary. Please consult a healthcare provider.")

    print("\nThank you for using the BMI Calculator!")

if __name__ == "__main__":
    main()

def additional_feature():
    print("This is an additional feature placeholder.")
    print("You can add more functionalities here.")

def repeat_calculation():
    while True:
        name, weight, height = get_user_input()
        bmi = calculate_bmi(weight, height)
        category = determine_bmi_category(bmi)
        display_results(name, bmi, category)
        
        if input("Do you want to calculate again? (yes/no): ").lower() != 'yes':
            break

def save_results_to_file(name, bmi, category):
    with open("bmi_results.txt", "a") as file:
        file.write(f"{name}, BMI: {bmi:.2f}, Category: {category}\n")

def load_previous_results():
    try:
        with open("bmi_results.txt", "r") as file:
            print("\nPrevious Results:")
            for line in file:
                print(line.strip())
    except FileNotFoundError:
        print("No previous results found.")

def main_with_options():
    print("Welcome to the BMI Calculator!")
    load_previous_results()
    
    while True:
        name, weight, height = get_user_input()
        bmi = calculate_bmi(weight, height)
        category = determine_bmi_category(bmi)
        display_results(name, bmi, category)
        save_results_to_file(name, bmi, category)

        if input("Do you want to calculate again? (yes/no): ").lower() != 'yes':
            break

if __name__ == "__main__":
    main_with_options()
