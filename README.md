---# User Management Application## Technologies Used- **Framework:** Spring Boot- **Language:** Java## Data FlowThe User Management Application follows a structured data flow pattern to handle user data and operations efficiently:### Application Entry PointThe application is initiated through the main class `UserManagementApplication`. It uses Spring Boot to run the application.```java@SpringBootApplicationpublic class UserManagementApplication {    public static void main(String[] args) {        SpringApplication.run(UserManagementApplication.class, args);    }}```### EnumerationsThe application defines two enums for gender and user type:#### Gender- Enumerates different genders: MALE, FEMALE, TRANS.```javapublic enum Gender {    MALE,    FEMALE,    TRANS}```#### Type- Enumerates user types: ADMIN, CUSTOMER, INTERNAL.```javapublic enum Type {    ADMIN,    CUSTOMER,    INTERNAL}```### User EntityThe `User` class represents the user entity with various attributes and validation constraints:- `userId`: An integer field marked as not null.- `userName`: A string field that must not be blank.- `userEmail`: A field validated as a valid email address.- `password`: A secure password field with specific constraints (at least one lowercase letter, one uppercase letter, one digit, one special character, and a minimum length of 8 characters).- `userContact`: A 10-digit contact number with numeric characters only.- `userGender`: An enum field representing user gender.- `userType`: An enum field representing user type.- `userDOB`: A field representing the user's date of birth.```java@Data@NoArgsConstructor@AllArgsConstructorpublic class User {    // Fields and validation constraints...}```### PasswordChangerThe `PasswordChanger` class represents a structure for changing a user's password. It contains the user's ID and a new password with similar password constraints as the `User` class.```java@Data@NoArgsConstructor@AllArgsConstructorpublic class PasswordChanger {    // Fields and validation constraints...}```### UserFactory ConfigurationA `UserFactory` configuration class provides an initial list of users. It is a Spring bean that initializes an empty list of users.```java@Configurationpublic class UserFactory {    @Bean    List<User> getUserListInit() {        return new ArrayList<>();    }}```### User RepositoryThe `UserRepo` class acts as a repository to manage user data. It is responsible for accessing and storing user information. It uses an in-memory list of users.```java@Repositorypublic class UserRepo {    @Autowired    private List<User> usrList;    public List<User> getUsrList() {        return usrList;    }}```### User ServiceThe `UserService` class provides services related to user management. It interacts with the `UserRepo` to access and manipulate user data.- `getAllUser()`: Retrieves a list of all users.- `addUsers(List<User> myUsers)`: Adds a list of users to the existing user list.- `updatePasswordByUserId(Integer id, String password)`: Updates the password of a user by their ID.```java@Servicepublic class UserService {    @Autowired    UserRepo userRepo;    // Methods...}```## Project SummaryThe User Management Application is built using Spring Boot and Java. It employs a structured data flow pattern to efficiently manage user data and operations. The application includes an entity class with validation constraints, a repository to manage data, and services to perform user-related operations.By following a well-defined data flow and validation constraints, this application helps streamline user management, including adding, updating, and retrieving user information. The application can be further extended and customized to meet specific user management requirements.---