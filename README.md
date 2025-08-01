Assignment 2: Kattangal Kafe - Kitchen Workflow System

Posted: Friday, August 1, 2025

Due: Friday, August 8, 2025

🎯 Objective
This assignment challenges you to model a dynamic, real-world workflow. Building upon basic class design, you will now focus on object states and interactions. You will practice:

System Modeling: Designing a multi-step process using Use Case and Class Diagrams.

Diagrams as Code: Creating these diagrams from scratch using PlantUML.

State Management: Modeling how objects transition between different states (e.g., an order moving from 'taken' to 'served').

Test-Driven Development (TDD): Applying TDD to complex functionalities involving collaboration between different classes.

📚 Background

The owner of Kattangal Kafe is pleased with the initial system but has identified a new bottleneck: the communication between the front desk and the kitchen. Orders written on paper slips get lost, and waiters don't know when food is ready, leading to delays and cold Pazham Poris.

Your task is to design and implement a system that manages the lifecycle of an order from the moment it's taken to the moment it's served, focusing on the creation and management of a Kitchen Order Ticket (KOT).

⚙️ Core Workflow to Model

Taking the Order: A waiter creates a new customer order. They add items along with their quantities (e.g., 2 Sulaimani, 4 Parippu Vada). At this stage, the order is considered OPEN.

Sending to Kitchen: Once the waiter confirms the order with the customer, they finalize it. This action generates a KOT for the kitchen. The original order's status is updated to CONFIRMED, and the new KOT is created with a status of QUEUED.

Kitchen Processing: The kitchen staff views the queue of KOTs. When they start preparing an order, they update the KOT's status to IN_PROGRESS. Once all items are cooked and plated, the status changes to READY_FOR_SERVING.

Serving the Order: The system notifies the waiter that an order is ready. The waiter picks up the food, serves it to the customer, and marks the KOT as SERVED, completing its lifecycle.

📊 Diagramming Requirements with PlantUML

You are required to create the following diagrams as code. 
You must write the PlantUML syntax yourself. 
Refer to the official PlantUML documentation for syntax and examples.



1. Use Case Diagram

Task: Model the interactions of the staff with the system.

Actors to Include: Waiter, Kitchen Staff.

Use Cases to Depict: Your diagram must clearly show the workflow, including creating orders, finalizing orders to generate a KOT, updating KOT status in the kitchen, and marking orders as served.

File: Create this diagram in diagrams/usecase.puml.

2. Class Diagram

Task: Model the static structure of your system. This is your blueprint for coding.

Classes to Consider: Think about what classes are needed. You'll likely need MenuItem, Order, and KitchenOrderTicket (KOT). How will you handle quantities? How will you represent the different statuses? 

An enum for status (OrderStatus, KOTStatus) is highly recommended.

Content: Your diagram must show the classes, their key attributes and methods, and the relationships between them (e.g., how an Order relates to a KOT).

File: Create this diagram in diagrams/class.puml.

🧪 TDD Practice Functionalities

You must use the TDD cycle (Red-Green-Refactor) to implement at least the following four functionalities. Create dedicated tests for each one.

Order Total Calculation with Quantities: An Order must accurately calculate its total price based on items and their respective quantities. For example, an order of 2 Chais (₹10 each) and 3 Uzhunnu Vadas (₹12 each) should correctly total ₹56.

Generation of KOT from an Order: An Order object must have a method that creates and returns a corresponding KOT object. The test must verify that the generated KOT contains the correct items and quantities and that its initial status is set to QUEUED.

KOT Status Lifecycle Management: The KOT class must correctly manage its status transitions. It should have methods to progress its status (e.g., startPreparation(), markAsReady()). Your tests must verify valid transitions (e.g., QUEUED to IN_PROGRESS) and prevent invalid ones (e.g., QUEUED to SERVED).

Filtering KOTs by Status: Create a KitchenManager class (or similar) that holds a list of active KOTs. This class must have a method, e.g., getReadyToServeKOTs(), that returns a new list containing only the KOTs with the status READY_FOR_SERVING. Your test should create multiple KOTs with varied statuses and assert that this method returns only the correct ones.

✅ Submission

Final Submission Checklist:

1. diagrams/usecase.puml file with your Use Case Diagram code.

2. diagrams/class.puml file with your Class Diagram code.

3. Completed Java code for all classes (Order, KOT, etc.).

4. Completed JUnit tests proving the four TDD functionalities are working correctly.

5. All tests are passing.

Final Commit and Push Instruction:

Once everything on the checklist is complete, make your final commit and push it to GitHub. This single push should contain all your completed work.