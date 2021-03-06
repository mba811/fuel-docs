
.. _heat-test-details:

Details of Heat platform tests
------------------------------

.. topic:: Typical stack actions: create, update, delete, show details, etc

  The test verifies that the Heat service can create, update and delete a stack
  and shows details of the stack and its resources, events and template.

  Target component: Heat

  Scenario:

  1. Create a stack.
  2. Wait for the stack status to change to 'CREATE_COMPLETE'.
  3. Get the details of the created stack by its name.
  4. Get the resources list of the created stack.
  5. Get the details of the stack resource.
  6. Get the events list of the created stack.
  7. Get the details of the stack event.
  8. Update the stack.
  9. Wait for the stack to update.
  10. Get the stack template details.
  11. Get the resources list of the updated stack.
  12. Delete the stack.
  13. Wait for the stack to be deleted.

.. topic:: Check stack autoscaling

  The test verifies that the Heat service can scale the stack capacity
  up and down automatically according to the current conditions.

  Target component: Heat

  Scenario:

  1. Image with cfntools package should be imported.
  2. Create a flavor.
  3. Create a keypair.
  4. Save the generated private key to a file on Controller node.
  5. Create a security group.
  6. Create a stack.
  7. Wait for the stack status to change to 'CREATE_COMPLETE'.
  8. Create a floating IP.
  9. Assign the floating IP to the instance of the stack.
  10. Wait for the cloud_init procedure to be completed on the instance.
  11. Load the instance CPU to initiate the stack scaling up.
  12. Wait for the second instance to be launched.
  13. Release the instance CPU to initiate the stack scaling down.
  14. Wait for the second instance to be terminated.
  15. Delete the file with the private key.
  16. Delete the stack.
  17. Wait for the stack to be deleted.

.. topic:: Check stack rollback

  The test verifies that the Heat service can rollback the stack
  if its creation failed.

  Target component: Heat

  Scenario:

  1. Start stack creation with rollback enabled.
  2. Verify the stack appears with status 'CREATE_IN_PROGRESS'.
  3. Wait for the stack to be deleted as a result of the rollback after the
     expiration of the timeout defined in the WaitHandle resource
     of the stack.
  4. Verify if the instance of the stack has been deleted.

.. topic:: Check advanced stack actions: suspend, resume

  The test verifies that the Heat service can suspend and resume the stack.

  Target component: Heat

  Scenario:

  1. Create a stack.
  2. Wait until the stack status changes to 'CREATE_COMPLETE'.
  3. Call stack suspend action.
  4. Wait until the stack status changes to 'SUSPEND_COMPLETE'.
  5. Call stack resume action.
  6. Wail until the stack status changes to 'RESUME_COMPLETE'.
  7. Call stack check action.
  8. Wail until the stack status changes to 'CHECK_COMPLETE'.
  9. Delete the stack and wait for the stack to be deleted.
