# BudgetTracker
A Budget Tracker is a Python application designed to help users manage their finances by recording income, expenses, and providing insights into spending patterns.
class BudgetTracker:
    def __init__(self):
        self.income=0
        self.expenses=[]
    def add_income(self):
        try:
            self.income=float(input("Enter your total income:$"))
        except valueError:
            print("Please enter a valid income!!!")
    def add_expense(self):
        while True:
            try:
                expense_name=input("Enter expense name (eg: Rent,Groceries,etc:")
                expense_amount=float(input(f"Enter the amount for {expense_name}:$"))
                self.expenses.append((expense_name,expense_amount))
                another=input("Do you want to add another expense?(y/n):").lower()
                if another !='y':
                    break
            except ValueError:
                print("Please enter a vaild expense!!!")
    def view_balance(self):
        total_expenses=sum(expense[1] for expense in self.expenses)
        balance=self.income-total_expenses
        print("\n Budget Summary:")
        print(f"Total income:${self.income:.2f}")
        print(f"Total Expenses:${total_expenses:.2f}")
        print(f"Remaining balance:${balance:.2f}")
    def show_expenses(self):
        print("\nExpenses Breakdown:")
        for name,amount in self.expenses:
            print(f"{name}:${amount:.2f}")
def main():
    tracker1=BudgetTracker()
    tracker1.add_income()
    tracker1.add_expense()
    tracker1.view_balance()
    tracker1.show_expenses()
if __name__ =="__main__":
    main()
