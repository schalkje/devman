# Speckit Usage Guide

Speckit is a tool designed to simplify and enhance your development workflow. This guide provides an overview of how to use Speckit effectively.

## Getting Started

Go to the [Speckit GitHub repository](https://github.com/schalkje/devman) for detailed setup instructions.

## Documentation

For detailed documentation, visit the [Speckit Documentation](https://github.com/schalkje/devman/blob/main/speckit/speckit.md).

## Examples

Here are some examples to help you get started:

- Example 1: How to use a specific feature.
- Example 2: Advanced usage scenarios.

For more examples, check the [examples section](https://github.com/schalkje/devman/blob/main/speckit/speckit.md#examples) in the documentation.

## Creating a New Spec

To create a new spec in Speckit, follow these steps:

1. **Navigate to the Speckit Directory**:
   Ensure you are in the `speckit` directory of the repository.
   ```bash
   cd speckit
   ```

2. **Run the Spec Creation Command**:
   Use the following command to create a new spec:
   ```bash
   speckit create <spec-name>
   ```
   Replace `<spec-name>` with the desired name for your spec.

3. **Edit the Spec File**:
   Open the newly created spec file in your preferred text editor and define the spec details.

4. **Validate the Spec**:
   Run the validation command to ensure the spec is correctly defined:
   ```bash
   speckit validate <spec-name>
   ```

5. **Commit the Spec**:
   Add the new spec to version control and commit the changes:
   ```bash
   git add specs/<spec-name>
   git commit -m "Add new spec: <spec-name>"
   ```

For more details, refer to the [Speckit Documentation](https://github.com/schalkje/devman/blob/main/speckit/speckit.md#creating-a-new-spec).

## Creating a New Spec from Another Spec Branch

When using Speckit with Claude from within VS Code, a Git branch is automatically created for each spec. To create a new spec from an existing spec branch, follow these steps:

1. **Switch to the Existing Spec Branch**:
   Ensure you are on the branch of the spec you want to base the new spec on:
   ```bash
   git checkout <existing-spec-branch>
   ```
   Replace `<existing-spec-branch>` with the name of the branch.

2. **Create a New Branch**:
   Create a new branch for the new spec:
   ```bash
   git checkout -b <new-spec-branch>
   ```
   Replace `<new-spec-branch>` with the desired name for the new spec branch.

3. **Create the New Spec**:
   Use the Speckit command to create the new spec:
   ```bash
   speckit create <new-spec-name>
   ```
   Replace `<new-spec-name>` with the name of the new spec.

4. **Edit and Validate the New Spec**:
   - Open the new spec file and make the necessary changes.
   - Validate the spec to ensure correctness:
     ```bash
     speckit validate <new-spec-name>
     ```

5. **Commit the Changes**:
   Add and commit the new spec to the branch:
   ```bash
   git add specs/<new-spec-name>
   git commit -m "Add new spec: <new-spec-name> based on <existing-spec-branch>"
   ```

6. **Push the New Branch**:
   Push the new branch to the remote repository:
   ```bash
   git push -u origin <new-spec-branch>
   ```

For more details, refer to the [Speckit Documentation](https://github.com/schalkje/devman/blob/main/speckit/speckit.md#creating-a-new-spec-from-another-branch).

## Support

If you encounter any issues, please open an issue on the [GitHub repository](https://github.com/schalkje/devman/issues).