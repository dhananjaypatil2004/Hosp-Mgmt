# Hosp-Mgmt
# Hospital Information Management System
# Developed by: Dhananjay Patil, Shreyanshu Owhal, Vinit Sanghai
# Under guidance of Prof. Raksha Dhulap

import datetime

patients = []
doctors = []
appointments = []

# -----------------------------
# Patient Management
# -----------------------------
def add_patient():
    pid = input("Enter Patient ID: ")
    name = input("Enter Patient Name: ")
    age = input("Enter Age: ")
    gender = input("Enter Gender (M/F): ")
    symptoms = input("Enter Symptoms: ")
    patients.append({
        "id": pid,
        "name": name,
        "age": age,
        "gender": gender,
        "symptoms": symptoms
    })
    print("\n✅ Patient added successfully!\n")

def view_patients():
    if not patients:
        print("No patient records found.")
        return
    print("\n--- Patient List ---")
    for p in patients:
        print(f"ID: {p['id']} | Name: {p['name']} | Age: {p['age']} | Gender: {p['gender']} | Symptoms: {p['symptoms']}")
    print()

def update_patient():
    pid = input("Enter Patient ID to update: ")
    for p in patients:
        if p["id"] == pid:
            p["name"] = input("Enter New Name: ")
            p["age"] = input("Enter New Age: ")
            p["gender"] = input("Enter New Gender: ")
            p["symptoms"] = input("Enter New Symptoms: ")
            print("✅ Patient details updated successfully!\n")
            return
    print("❌ Patient not found.\n")

def delete_patient():
    pid = input("Enter Patient ID to delete: ")
    for p in patients:
        if p["id"] == pid:
            patients.remove(p)
            print("✅ Patient record deleted successfully!\n")
            return
    print("❌ Patient not found.\n")

# -----------------------------
# Doctor Management
# -----------------------------
def add_doctor():
    did = input("Enter Doctor ID: ")
    name = input("Enter Doctor Name: ")
    specialty = input("Enter Specialty: ")
    doctors.append({
        "id": did,
        "name": name,
        "specialty": specialty
    })
    print("\n✅ Doctor added successfully!\n")

def view_doctors():
    if not doctors:
        print("No doctor records found.")
        return
    print("\n--- Doctor List ---")
    for d in doctors:
        print(f"ID: {d['id']} | Name: {d['name']} | Specialty: {d['specialty']}")
    print()

# -----------------------------
# Appointment Management
# -----------------------------
def book_appointment():
    pid = input("Enter Patient ID: ")
    did = input("Enter Doctor ID: ")
    date = input("Enter Appointment Date (YYYY-MM-DD): ")
    appointments.append({
        "pid": pid,
        "did": did,
        "date": date
    })
    print("✅ Appointment booked successfully!\n")

def view_appointments():
    if not appointments:
        print("No appointments found.")
        return
    print("\n--- Appointment List ---")
    for a in appointments:
        patient_name = next((p['name'] for p in patients if p['id'] == a['pid']), "Unknown")
        doctor_name = next((d['name'] for d in doctors if d['id'] == a['did']), "Unknown")
        print(f"Patient: {patient_name} | Doctor: {doctor_name} | Date: {a['date']}")
    print()

# -----------------------------
# Simple AI-based Health Feedback
# -----------------------------
def ai_health_feedback():
    symptom = input("Enter your symptom: ").lower()
    if "fever" in symptom or "cold" in symptom:
        print("🤖 Suggestion: You may have viral fever. Drink fluids and rest. See a doctor if it persists.")
    elif "headache" in symptom:
        print("🤖 Suggestion: Possibly migraine or stress. Stay hydrated and relax.")
    elif "cough" in symptom:
        print("🤖 Suggestion: Could be throat infection. Warm fluids may help.")
    elif "stomach" in symptom:
        print("🤖 Suggestion: Could be indigestion. Avoid spicy food and drink water.")
    else:
        print("🤖 Suggestion: Please consult a doctor for accurate diagnosis.")
    print()

# -----------------------------
# Main Menu
# -----------------------------
def main_menu():
    while True:
        print("===== Hospital Information Management System =====")
        print("1. Add Patient")
        print("2. View Patients")
        print("3. Update Patient")
        print("4. Delete Patient")
        print("5. Add Doctor")
        print("6. View Doctors")
        print("7. Book Appointment")
        print("8. View Appointments")
        print("9. AI Health Feedback")
        print("0. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            add_patient()
        elif choice == "2":
            view_patients()
        elif choice == "3":
            update_patient()
        elif choice == "4":
            delete_patient()
        elif choice == "5":
            add_doctor()
        elif choice == "6":
            view_doctors()
        elif choice == "7":
            book_appointment()
        elif choice == "8":
            view_appointments()
        elif choice == "9":
            ai_health_feedback()
        elif choice == "0":
            print("👋 Exiting System. Thank you!")
            break
        else:
            print("❌ Invalid choice. Try again.\n")

# Run program
if __name__ == "__main__":
    main_menu()
