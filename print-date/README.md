# PrintDate

## Goals
Be able to test printCurrentDate function without changing the method signature.

1.- Test the code using test doubles created by you.

2.- Test the code using test doubles created using a test library.

## Code to test 
    void printCurrentDate(){
        time_t now = this->calendar->today();
        char *timeNow = ctime(&now);
        this->printer->printLine(timeNow);
    }

## Run the tests

Use make or read the [Makefile](./Makefile)
    
## Tools
[gMock](https://google.github.io/googletest/gmock_cheat_sheet.html)

### Example of Mock in GoogleTest (C++)

    class EmailSender {
    public:
        virtual void send(Email*) const = 0;
    };
    
    class MockEmailSender : public EmailSender {
    public:
    
        MOCK_METHOD(void, send, (Email*), (const, override));
    };


    TEST(UserRegistrationTest, should_send_an_email) {
        MockEmailSender emailSender;
        userRegistration = UserRegistration(&email_sender)
    
        EXPECT_CALL(emailSender, send())
            .Times(1);
    
        userRegistration.register()
    }



	
### Example of Stub in GoogleTest (C++)

    class PasswordValidator {
    public:
        virtual bool isValid(char*) const = 0;
    };
    
    class StubPasswordValidator : public PasswordValidator {
    public:
    
        MOCK_METHOD(bool, isValid, (char*), (const, override));
    };


    TEST(UserRegistrationTest, should_succeed_when_password_is_valid) {
        StubPasswordValidator passwordValidator;
        userRegistration = UserRegistration(&passwordValidator)
        
        EXPECT_CALL(passwordValidator, isValid())
            .WillRepeatedly(Return(True));
    
        bool succeed = userRegistration.register()
    
        EXPECT_TRUE(succeed);
    }

# Author
Codium [@codiumteam](https://www.twitter.com/codiumteam)