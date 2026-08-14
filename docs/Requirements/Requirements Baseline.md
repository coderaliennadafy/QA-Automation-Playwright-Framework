# Requirements Baseline

## 1. Customer Account & Authentication

### AUTH-001 — Customer Registration

Requirement ID: AUTH-001

Title: Customer Registration

Description / Requirement Statement:
The system shall allow a guest customer to create a customer account
by submitting the required registration information.

Business Domain / Module:
Customer Account & Authentication

Actor:
Guest Customer

Preconditions:
- Customer is not authenticated.
- Registration is enabled.

Trigger:
Customer submits the registration form.

Expected Business Behavior:
- The system validates the submitted registration information.
- A valid registration creates a customer account.
- Invalid registration data prevents account creation.
- Appropriate validation feedback is displayed.

Business Rules:
- Required registration information must be provided.
- Email must use a valid format.
- Password confirmation must match the password.

Priority:
High

Risk:
High

Acceptance Criteria:
- Guest customer can access the registration page.
- Required fields are validated.
- Valid information creates an account.
- Invalid information prevents registration.
- Validation feedback is displayed.

Dependencies:
- Customer account persistence
- Authentication service

Source / Reference:
- nopCommerce demo registration flow
- Existing manual registration coverage
- Test Scope

Automation Candidate:
Yes

Notes:
Critical customer acquisition workflow.

### AUTH-002 — Registration Input Validation

Requirement ID: AUTH-002

Title: Registration Input Validation

Description / Requirement Statement:
The system shall validate customer registration input before creating
a customer account and shall prevent account creation when submitted
data does not satisfy the required validation rules.

Business Domain / Module:
Customer Account & Authentication

Actor:
Guest Customer

Preconditions:
- Customer is not authenticated.
- Customer is on the registration page.
- Registration is enabled.

Trigger:
Customer submits the registration form with registration information.

Expected Business Behavior:
- The system validates all submitted registration data.
- Required fields are validated before account creation.
- Invalid field values prevent successful registration.
- Appropriate validation feedback is displayed for invalid input.
- Valid registration data can proceed to account creation.

Business Rules:
- Required registration fields must not be empty.
- Email address must follow the supported email format.
- Password must satisfy the configured password requirements.
- Password confirmation must match the password.
- Invalid registration input must not result in customer account creation.

Priority:
High

Risk:
High

Acceptance Criteria:
- Submission with missing required information is rejected.
- Submission with an invalid email format is rejected.
- Submission with an invalid password is rejected when password rules
  are not satisfied.
- Submission with mismatched password confirmation is rejected.
- Validation feedback identifies the relevant invalid input.
- A registration containing valid required information can proceed
  successfully.
- No customer account is created when validation fails.

Dependencies:
- Registration form
- Customer account validation
- Customer account persistence
- Configured password policy

Source / Reference:
- nopCommerce registration flow
- Existing manual registration test coverage
- Test Scope
- Customer Account & Authentication requirements

Automation Candidate:
Yes

Notes:
Validation should be covered through positive, negative, and boundary
test scenarios. UI automation should validate user-facing behavior,
while API-level validation may be added where the corresponding API
is available and in scope.

### AUTH-003 — Duplicate Customer Email Prevention

Requirement ID: AUTH-003

Title: Duplicate Customer Email Prevention

Description / Requirement Statement:
The system shall prevent the creation of multiple customer accounts
using the same email address when the email is already associated
with an existing customer account.

Business Domain / Module:
Customer Account & Authentication

Actor:
Guest Customer

Preconditions:
- Registration is enabled.
- A customer account already exists with the submitted email address.
- The customer is not authenticated.

Trigger:
The customer submits the registration form using an email address
that is already associated with an existing customer account.

Expected Business Behavior:
- The system checks whether the submitted email address is already
  associated with an existing customer account.
- Registration is rejected when the email address is already in use.
- The existing customer account remains unchanged.
- Appropriate validation feedback is displayed to the customer.
- No duplicate customer account is created.

Business Rules:
- A customer email address must be unique where unique-email
  registration is enabled.
- An email address already associated with a customer account
  must not create another account.
- Failed registration due to a duplicate email must not modify
  the existing customer account.
- The duplicate-email validation must occur before successful
  account creation.

Priority:
High

Risk:
High

Acceptance Criteria:
- Registration with an unused email address can proceed when all
  other required information is valid.
- Registration with an email address already associated with an
  existing customer account is rejected.
- Appropriate validation feedback is displayed when the email
  address is already in use.
- No additional customer account is created after a duplicate
  email registration attempt.
- The existing customer account remains accessible and unchanged.
- Repeated attempts using the same existing email continue to be
  rejected according to the configured registration rules.

Dependencies:
- Customer account persistence
- Customer registration functionality
- Email uniqueness configuration
- Registration validation

Source / Reference:
- nopCommerce customer registration flow
- Existing manual registration coverage
- Test Scope
- Customer Account & Authentication requirements

Automation Candidate:
Yes

Notes:
This requirement should be covered by positive and negative
registration scenarios. The test data should include both a known
existing customer email and a unique email address. The behavior
depends on the application's configured email uniqueness rules