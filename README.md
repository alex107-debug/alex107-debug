import json

# Beispiel-Datenbank für Tuning-Club
tuning_database = {}

# Funktion, um ein Fahrzeug hinzuzufügen
def add_vehicle():
    print("\nFahrzeug Hinzufügen")
    vehicle_name = input("Name des Fahrzeugs: ")
    tuning_parts = input("Geben Sie die verbauten Tuning-Teile an (z. B. Spoiler, Felgen, Auspuff): ").split(',')
    engine_tuning = input("Geben Sie die Motor-Tuning-Daten ein (z. B. PS, Turbo): ")
    
    vehicle_data = {
        'name': vehicle_name,
        'tuning_parts': [part.strip() for part in tuning_parts],
        'engine_tuning': engine_tuning
    }
    
    tuning_database[vehicle_name] = vehicle_data
    print(f"\n{vehicle_name} wurde erfolgreich hinzugefügt!")

# Funktion, um ein Fahrzeug zu bearbeiten
def edit_vehicle():
    print("\nFahrzeug Bearbeiten")
    vehicle_name = input("Geben Sie den Namen des Fahrzeugs ein, das Sie bearbeiten möchten: ")
    
    if vehicle_name in tuning_database:
        print(f"\nBearbeite Fahrzeug: {vehicle_name}")
        new_tuning_parts = input("Geben Sie neue Tuning-Teile an (z. B. Spoiler, Felgen, Auspuff): ").split(',')
        new_engine_tuning = input("Geben Sie die neuen Motor-Tuning-Daten ein (z. B. PS, Turbo): ")

        tuning_database[vehicle_name]['tuning_parts'] = [part.strip() for part in new_tuning_parts]
        tuning_database[vehicle_name]['engine_tuning'] = new_engine_tuning
        print(f"\n{vehicle_name} wurde erfolgreich bearbeitet!")
    else:
        print("\nFahrzeug nicht gefunden!")

# Funktion, um ein Fahrzeug anzuzeigen
def view_vehicle():
    print("\nFahrzeug Anzeigen")
    vehicle_name = input("Geben Sie den Namen des Fahrzeugs ein, das Sie anzeigen möchten: ")
    
    if vehicle_name in tuning_database:
        vehicle_data = tuning_database[vehicle_name]
        print(f"\nFahrzeugname: {vehicle_data['name']}")
        print(f"Tuning-Teile: {', '.join(vehicle_data['tuning_parts'])}")
        print(f"Motor-Tuning: {vehicle_data['engine_tuning']}")
    else:
        print("\nFahrzeug nicht gefunden!")

# Funktion, um alle Fahrzeuge anzuzeigen
def view_all_vehicles():
    print("\nAlle Fahrzeuge im Tuning-Club")
    if tuning_database:
        for vehicle_name, vehicle_data in tuning_database.items():
            print(f"\nFahrzeugname: {vehicle_data['name']}")
            print(f"Tuning-Teile: {', '.join(vehicle_data['tuning_parts'])}")
            print(f"Motor-Tuning: {vehicle_data['engine_tuning']}")
    else:
        print("Keine Fahrzeuge im System!")

# Menü für den Tuning-Club
def show_menu():
    print("\nTuning-Club Online")
    print("1. Fahrzeug hinzufügen")
    print("2. Fahrzeug bearbeiten")
    print("3. Fahrzeug anzeigen")
    print("4. Alle Fahrzeuge anzeigen")
    print("5. Beenden")
    
    choice = input("\nWählen Sie eine Option (1-5): ")

    if choice == '1':
        add_vehicle()
    elif choice == '2':
        edit_vehicle()
    elif choice == '3':
        view_vehicle()
    elif choice == '4':
        view_all_vehicles()
    elif choice == '5':
        print("Tuning-Club beendet.")
        return False
    else:
        print("Ungültige Auswahl. Versuchen Sie es erneut.")
    
    return True

# Hauptprogramm-Schleife
def main():
    while True:
        if not show_menu():
            break

if __name__ == "__main__":
    main()
