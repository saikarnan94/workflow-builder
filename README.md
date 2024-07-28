# Workflow Builder

A Vue.js-based workflow builder application that allows users to drag and drop various components to create custom workflows. The application utilizes Vuetify for the UI components and supports draggable and resizable elements.

![Workflow Builder Screenshot](workflow_builder_screenshot.png)

## Features

- **Drag and Drop**: Easily drag components from the sidebar onto the canvas.
- **Resizable Components**: Adjust the size of the components on the canvas.
- **Persistent State**: Save and load the canvas state to and from local storage.
- **Customizable Components**: Various shapes and connections to choose from, including rectangles, circles, and arrows.
- **Banner Note**: Display a persistent note on the canvas with a close button.

## Components

- **Shapes**: Rectangle, Circle, Parallelogram, Diamond, etc.
- **Connections**: Right Arrow, Left Arrow, Up Arrow, Down Arrow, Bidirectional Arrow.
- **TextBox**: An input field for entering text.

## Installation

To get started with the Workflow Builder, follow these steps:

1. **Clone the repository**:
    ```bash
    git clone https://github.com/saikarnan94/workflow-builder.git
    ```

2. **Navigate to the project directory**:
    ```bash
    cd workflow-builder
    ```

3. **Install the dependencies**:
    ```bash
    npm install
    ```

4. **Run the development server**:
    ```bash
    npm run dev
    ```

5. **Open your browser** and navigate to localhost URL provided.

## Usage

### Drag and Drop

- Drag components from the sidebar and drop them onto the canvas.
- Components can be resized by dragging their corners.

### Save and Load Canvas State

- Use the `Save` button to save the current state of the canvas to local storage.
- Use the `Load` button to load the saved state from local storage.
- Use the `Clear` button to clear the canvas.

### Edit Text

- Double-click on the `TextBox` component to edit the text.

### Close Banner Note

- Click the close button on the banner note to remove it from the canvas.