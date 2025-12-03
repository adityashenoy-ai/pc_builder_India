# pc_builder_India

₹ Indian PC Builder Wizard
This is a single-page web application designed to help users in India build a custom Personal Computer (PC) by selecting compatible components step-by-step. It provides a real-time visualization of the build, calculates the total estimated price, and performs essential compatibility checks for components like CPU, Motherboard, and RAM.

The application is built using plain JavaScript for logic and Tailwind CSS for a clean, modern, dark-themed UI, ensuring a fast and interactive user experience.

✨ Features
Step-by-Step Wizard: Guides the user through the selection of seven core PC components in a logical order.

Real-time Visualization: A dynamic SVG display on the right pane shows selected components (CPU, GPU, RAM, etc.) inside a virtual PC case. * Compatibility Checking: Automatically checks for critical mismatches, such as:


CPU-Motherboard Socket Mismatch 





Motherboard-RAM DDR Type Mismatch 




PSU Wattage Sufficiency against the estimated total TDP (CPU + GPU + Base).





Multi-Select Component (RAM): Allows users to select multiple RAM sticks of different types and quantities, adhering to the motherboard's maximum slot count.



Real-time Price and TDP Total: Calculates and displays the total estimated cost in ₹ (Indian Rupee). It also provides a Total TDP Estimate and the PSU Capacity.





Simulated Product Data: Uses simulated product names, specifications, and prices based on current Indian market trends.

💻 Tech Stack

HTML5 


Tailwind CSS (via CDN): Used for rapid and responsive styling, providing a dark, tech-aesthetic theme.


Vanilla JavaScript: Powers all the application logic, state management, UI rendering, and compatibility checks.


SVG (Scalable Vector Graphics): Used for the dynamic PC case visualization, allowing components to be visually "added" or "removed" by changing SVG element attributes (like opacity and fill color).


🛠️ Components Selection Steps
The builder follows a fixed, logical order for component selection:


CPU (Processor): The core of the system.


Motherboard: The foundation that determines compatibility for the socket and RAM type.


RAM (Memory): Supports multi-selection for multiple sticks.


GPU (Graphics Card): Critical for gaming/heavy tasks; impacts PSU choice.


Storage (SSD/HDD): For the OS and files.


PSU (Power Supply): Must cover the total estimated wattage.


Case: The final enclosure.

🎨 Design and Styling Notes
The application uses a dark theme optimized for a technology-focused interface.


Primary Blue: #2563eb is used for active steps and primary buttons.


Success Green: #047857 and #1a202c are used for completed steps and price totals.


Visual Feedback: Selected parts in the component list are highlighted with a blue border/ring (ring-2 ring-blue-500).


Removal Icons: Visual components in the SVG have small, red 'X' icons that appear on hover, linked to the unselectPart() function, allowing users to quickly remove a component from the build.


⚙️ Key JavaScript Logic
The core of the application resides in the buildState object and several functions:

buildState: A central state object that holds the currently selected part for each category (e.g., buildState.cpu, buildState.motherboard). RAM is an array to support multiple sticks.



checkCompatibility(newPart, category): This function contains the crucial logic for socket, DDR, and wattage checks. It returns an object with compatible: boolean and a reason: string if incompatible.




selectPart(category, partId): Updates the buildState and triggers a re-render. Crucially, if a new CPU or Motherboard is selected, it invalidates dependent components (RAM, GPU, PSU) if they become incompatible, forcing the user to re-select.



updateSummary(): Iterates through the buildState to update the total price, TDP/wattage display, and the SVG visualization elements (changing opacity, fill color, and stroke).



adjustRamQuantity(partId, delta): Specific function to handle the increment/decrement controls for RAM sticks, ensuring the total count does not exceed the Motherboard's max slots.
