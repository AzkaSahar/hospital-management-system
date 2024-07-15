# hospital-management-system
Made by group of 3 people
# 1. Introduction:
The Hospital Management System is a comprehensive software solution designed to streamline and optimize various aspects of hospital operations, ranging from patient management to doctor appointments and emergency services. Leveraging data structures and algorithms and OOP concepts, this project aims to enhance the efficiency and functionality of the hospital's day-to-day activities.
# 2. Key Features:
- Unordered Maps for Data Storage and Retrieval:
The project employs the use of C++ unordered maps to store and manage critical data, such as patient, doctor, and nurse information. Unordered maps provide constant time complexity for average case lookups, significantly improving the speed of data retrieval.
- Priority Queue for Emergency OPD:
In emergency situations, patient prioritization is crucial. A priority queue is implemented to manage emergency cases efficiently. Patients are prioritized based on the severity of their condition, ensuring that critical cases receive
prompt attention.
- Binary Search Tree (BST) for Doctor Specialization:
To facilitate the quick retrieval of doctors based on their medical specialization, a Binary Search Tree (BST) is utilized. This allows for logarithmic time complexity in searching for doctors with specific expertise, optimizing the process of matching patients with suitable healthcare providers.
- Graphs for Ambulance Routing:
Graph data structures are employed to model the ambulance routes within the hospital. Shortest path algorithms are implemented to guide ambulances efficiently to specific locations, reducing response times during emergencies.
# 3. Components:
1. Patient Management:
Patients can be efficiently registered and managed within the system. Their personal details, medical history, and current status are stored, enabling seamless access for hospital staff.
2. Doctor and Nurse Management:
The system allows for the registration and tracking of doctors and nurses. Details such as specialization, availability, and appointments are efficiently
managed, contributing to an organized healthcare environment.
3. Appointment Scheduling:
Patients can schedule appointments with doctors, and the system ensures that appointments are managed effectively, preventing overbooking and
scheduling conflicts.
4. Emergency Services:
The project prioritizes emergency cases by utilizing a priority queue. Critical patients are promptly attended to, ensuring that emergency medical services
operate smoothly.
5. Graph-Based Ambulance Routing:
Ambulance routes are optimized using graph structures. Shortest path algorithms guide ambulances to their destinations, minimizing response times
during emergencies.
# 4. Classes:
1. ### Class Ambulance

#### Description
The `Ambulance` class represents an ambulance within the hospital's dispatch system. It manages the state of each ambulance, tracks its location, and facilitates emergency dispatch operations.

#### Private Fields
- `int id`: Unique identifier for the ambulance.
- `string vrn`: Vehicle registration number.
- `bool idle`: Operational status (idle or active).
- `string address`: Current location or destination.

#### Public Methods
- `Ambulance()`: Default constructor initializing with default values.
- `Ambulance(int id, string vrn, bool idle)`: Parameterized constructor to set specific values.
- `void fillMap()`: Reads ambulance data from `ambulances.dat` and populates the map.
- `void saveMap()`: Saves the current map of ambulances to `ambulances.dat`.
- `void addAmbulance()`: Adds a new ambulance to the system.
- `void printDetails()`: Prints details including ID, registration number, and status.
- `void send()`: Dispatches an ambulance to a specified destination.
- `void reportArrival()`: Updates ambulance status upon arrival.
- `void removeAmbulance()`: Removes an idle ambulance from the system.

#### Usage in Context
- The `Ambulance` class integrates with the hospital's ambulance management system to handle dispatch, location tracking, and status updates efficiently.
- It interacts with other components like the graph-based city model (`citygraph.dijkstra`) to optimize ambulance routes.

#### Practical Application
- Facilitates real-time ambulance dispatch and tracking.
- Integrates with external systems for route optimization and emergency response management.

2. ### Class person:
- **Description**: The `person` class serves as an abstract base class to represent a general person with attributes like ID, name, gender, age, contact information, and category (e.g., doctor, patient, nurse). It provides methods for adding and displaying details of a person. As an abstract class, it defines virtual methods to be implemented by derived classes, which handle specific types of persons.

- **Protected Fields**:
  - `int id`: Unique identifier for the person.
  - `string firstName`: The first name of the person.
  - `string lastName`: The last name of the person.
  - `char gender`: Gender of the person ('M' for male, 'F' for female).
  - `int age`: Age of the person.
  - `int mobNumber`: Mobile number of the person.
  - `string address`: Address of the person.
  - `string cat`: A string representing the category of the person (e.g., "doctor", "patient", "nurse").
  - `int category`: Numeric code for the category (1 for doctor, 2 for patient, 3 for nurse).

- **Public Methods**:
  - **person()**: Default constructor initializing the person with a default ID value of -1.
  - **virtual void fillMap() = 0**: Pure virtual method to populate a map with person data. Must be implemented by derived classes.
  - **virtual void saveMap() = 0**: Pure virtual method to save the current map of persons to a file. Must be implemented by derived classes.
  - **virtual void addPerson(int minAge = 0, int maxAge = 1000)**: Adds a new person to the system. Takes optional parameters to define age limits for the person being added, with default limits set from 0 to 1000 years.
    - Prompts for and validates the first name, last name, age (within specified limits), gender, mobile number, and address.
    - Ensures the age is appropriate for the person's category if not a patient.
  - **virtual void printDetails()**: Prints the details of the person including ID, full name, gender, age, mobile number, and address.
  - **virtual void printDetailsFromHistory()**: Prints historical details of the person, useful for audit or review purposes.
  - **virtual void getDetails() = 0**: Pure virtual method to retrieve specific details of a person. Must be implemented by derived classes.
  - **virtual void removePerson() = 0**: Pure virtual method to remove a person from the system. Must be implemented by derived classes.

### Usage in Context:
- The `person` class acts as a base class for more specific person types (like doctor, patient, or nurse). It provides common functionality and enforces a structure through pure virtual methods that derived classes must implement.
- This class handles the basic data entry and display functions, leaving the storage and retrieval mechanisms to be defined by the subclasses.
- Derived classes would need to implement `fillMap()`, `saveMap()`, `getDetails()`, and `removePerson()` to manage the specific requirements for their category (e.g., how a doctor is added and stored versus a patient).
  
3. ### Subclasses of Person:
a. Class Doctor:
- **Description**: This class represents a doctor and inherits from the Person class.
- Additional Fields: (specific to a doctor)
- Additional Methods: (specific to a doctor)
b. Class Patient:
- **Description**: This class represents a patient and inherits from the Person class.
- Additional Fields: (specific to a patient)
- Additional Methods: (specific to a patient)
c. Class Nurse:
- **Description**: This class represents a nurse and inherits from the Person class.
- Additional Fields: (specific to a nurse)
- Additional Methods: (specific to a nurse)
  
4. ### Class appointment:

- **Description**: The `appointment` class encapsulates the details and management of appointments between patients and doctors. It includes methods for booking appointments, storing and retrieving appointment details, and interacting with the hospital's appointment system.

- **Private Fields**:
  - `int id`: Unique identifier for the appointment.
  - `doctor D`: A `doctor` object representing the doctor associated with the appointment.
  - `patient P`: A `patient` object representing the patient associated with the appointment.
  - `int hh`: Start hour of the appointment in a 24-hour format (e.g., 9 for 9 AM, 14 for 2 PM).

- **Public Methods**:
  - **appointment()**: Default constructor initializing the appointment with default values (`id` = -1, `D.id` = -1, `P.id` = -1). This sets up the appointment with no specific doctor or patient initially.
  - **~appointment()**: Destructor that resets the appointment details (`id` = -1, `D.id` = -1, `P.id` = -1) when an appointment object is destroyed.
  - **void fillMap()**: Reads appointment data from a binary file (`appointments.dat`) and populates a map with the appointment details. This ensures that all previously saved appointments are loaded into the system.
  - **void saveMap()**: Saves the current map of appointments to a binary file. This method serializes the appointment data to ensure data persistence across sessions.
  - **void printDetails()**: Prints detailed information about the appointment including the appointment ID, patient's name and ID, doctor's name and ID, and the appointment time.
  - **void book()**: Handles the booking of a new appointment. This method:
    - Checks if any doctors are available for new appointments.
    - Registers a new patient or retrieves an existing patient's details.
    - Searches for and selects an available doctor.
    - Assigns a unique ID to the new appointment.
    - Schedules the appointment and updates the doctor's booked appointments.
    - Saves the appointment to the system and prints the details.
  - **void getDetails()**: Prompts the user to search for an appointment by its ID and retrieves its details from the map of appointments.

5. ### Class DoctorBST:
#### Key Components:

1. **Nested Structure**:
   - **Node**: Represents a node in the binary search tree.
     - **doctors**: A list storing doctors with the same specialization.
     - **left**: Pointer to the left child node.
     - **right**: Pointer to the right child node.

2. **Public Members**:
   - **root**: Pointer to the root node of the BST.

3. **Methods**:
   - **DoctorBST()**: Constructor to initialize the BST.
   - **insert(const doctor& doctor)**: Inserts a new doctor into the BST.
   - **insertRecursive(Node* node, const doctor& d)**: Helper function for recursive insertion.
   - **Search(const std::string& specialization) const**: Searches for doctors based on specialization and prints their details.

#### Functionality Details:

1. **Initialization**:
   - The `DoctorBST` object initializes with a null root pointer, indicating an empty BST initially.

2. **Insertion**:
   - **insert(const doctor& doctor)**: Inserts a doctor into the BST based on their specialization. If a node with the same specialization exists, the doctor is added to the existing list of doctors in that node.

3. **Search and Print**:
   - **Search(const std::string& specialization)**: Searches for doctors with a specific specialization within the BST. If found, it prints details of all doctors with that specialization.

#### Practical Application:

- **Organizing Doctors**: Helps organize doctors efficiently based on their specialization, facilitating quick retrieval and management.
- **Search Functionality**: Supports searching for doctors by specialization, essential for scheduling appointments or finding specialized medical care.
- **Dynamic Structure**: Being a BST, it allows dynamic addition and removal of doctors while maintaining sorted order, suitable for applications requiring flexibility and efficiency.

6.  ### Class hospital:

The `hospital` class serves as a centralized entity to manage various aspects of a hospital, including doctors, patients, nurses, appointments, and ambulances.

#### Private Members:

- **doctorsList**: `unordered_map<int, doctor>` - Stores doctors indexed by their unique ID.
- **patientsList**: `unordered_map<int, patient>` - Stores patients indexed by their unique ID.
- **nursesList**: `unordered_map<int, nurse>` - Stores nurses indexed by their unique ID.
- **appointmentsList**: `unordered_map<int, appointment>` - Stores appointments indexed by their unique ID.
- **ambulancesList**: `unordered_map<int, ambulance>` - Stores ambulances indexed by their unique ID.

#### Constants:

- **doctorsLimit**: `const int` - Maximum number of doctors allowed in the hospital.
- **nursesLimit**: `const int` - Maximum number of nurses allowed in the hospital.
- **ambulancesLimit**: `const int` - Maximum number of ambulances available.
- **appointmentsLimit**: `const int` - Maximum number of appointments that can be scheduled per day.

#### Friends:

- **doctor**, **patient**, **nurse**, **ambulance**, **appointment**, **emergencyOPD**, **graph**, **emergencypriorityqueue**: Granting access to private members for these classes.

#### Public Members:

- **doctorTree**: `static DoctorBST` - Static instance of `DoctorBST` for organizing doctors by specialization.

#### Methods:

- **hospital()**: Constructor initializes sample data for doctors, nurses, patients, and ambulances.
- **printDoctors()**: Prints details of all doctors currently stored.
- **printPatients()**: Prints details of all patients currently stored.
- **printNurses()**: Prints details of all nurses currently stored.
- **printAppointments()**: Prints details of all appointments currently scheduled.
- **printAmbulances()**: Prints details of all ambulances currently available.

#### Practical Application:

- **Centralized Management**: Provides a structured approach to manage hospital resources.
- **Integration with Specializations**: Uses `DoctorBST` to efficiently manage doctors based on their specialization.
- **Data Representation**: Utilizes unordered maps to store and retrieve information about doctors, patients, nurses, appointments, and ambulances.
- **Limit Handling**: Defines limits for maximum resources like doctors, nurses, ambulances, and appointments, ensuring efficient hospital operations.

7. ### Class Graph:

The `Graph` class represents a weighted graph structure using adjacency lists and provides methods for adding vertices and finding the shortest path between vertices using Dijkstra's algorithm.

#### Public Members:

- **vertices**: `unordered_map<string, unordered_map<string, int>>` - Stores vertices and their respective neighbors with edge weights.

#### Methods:

- **Graph()**: Default constructor.
- **addVertex(const string &name, const unordered_map<string, int> &edges)**: Adds a vertex to the graph with its associated edges and weights.
- **dijkstra(const string &start, const string &end)**: Computes the shortest path from `start` vertex to `end` vertex using Dijkstra's algorithm. Returns a pair containing the path as a vector of strings and the total distance as an integer.

#### Practical Application:

- **Graph Representation**: Utilizes adjacency lists (`vertices`) to represent the graph, where each vertex maps to its neighboring vertices along with their respective edge weights.
- **Pathfinding with Dijkstra's Algorithm**: Implements Dijkstra's algorithm to find the shortest path between vertices based on edge weights, ensuring efficient route planning in transportation or navigation scenarios.
- **Dynamic Graph Operations**: Supports dynamic addition of vertices and their connections, facilitating real-time updates in graph structure and pathfinding computations.

8. ### Class emergencyOPD:

#### Public Members:

- **emergencyqueue**: An instance of `emergencypriorityqueue` to store emergency patients in priority order.

#### Methods:

- **addemergencypatient(string name, int elevel)**: Registers a new emergency patient with the given `name` and `elevel` (emergency level). Pushes the patient into `emergencyqueue` and assigns an available OPD doctor to handle the case.
  
- **processnext()**: Processes the next emergency case from `emergencyqueue`. Prints details of the patient being processed. Marks the assigned doctor as available once the case is handled.

#### Friend Classes:

- **doctor**, **nurse**, **patient**, **person**: These classes have access to private members of `emergencyOPD` for efficient interaction.

#### Practical Application:

- **Emergency Case Management**: Handles incoming emergency cases efficiently using a priority queue based on their severity levels.
- **Doctor Assignment**: Automatically assigns an available OPD doctor to handle each emergency case.
- **Real-time Updates**: Keeps doctors' availability status updated based on whether they are currently handling a case or available for the next patient.


# 4. Conclusion:
The Hospital Management System project leverages data structures and algorithms to create a robust and efficient healthcare management solution. The use of unordered maps, priority queues, binary search trees, and graphs contributes to the overall effectiveness of the system, enhancing patient careand hospital operations. The class-based structure allows for extensibility and flexibility in adding new features or entities. This project serves as a comprehensive tool for hospitals to manage their resources, streamline processes, and provide quality healthcare services.
