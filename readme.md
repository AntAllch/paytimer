STEPS

create an form (with an id of earningsForm) with 
    - a label and input for (label "for" MUST match input "id")
        - shift time in hours
        - hourly rate
        - unpaid break start (how many hours from the START of your shift your timer pauses)
        - unpaid break end (how many hours from the START of your shift your timer resumes)

    - buttons for
        - Start timer (type submit)
        - End timer (type button) (with an id of stopTracker and a "disabled" attribute)

    - Earnings text with id of earningsDisplay
    - Countdown text timer with id of timer

----------------------------------------------------------------------------------------------------------------

in JS file
    - create const variables that target 
        - the form div itself
        - the end timer button
        - the earnings display
        - the countdown timer
    
    - create let variables with no value for
        - earnings interval
        - countdown interval

----------------------------------------------------------------------------------------------------------------

    - create an event listener on the earnings form that listens for a "submit" event and do the following:
    
        - prevent the page from refreshing

        - create variables that target the user inputs from
            - shift hours
            - hourly rate
            - break start
            - break end

        - create variables that convert
            - shift hours into seconds
            - break start into seconds
            - break end into seconds

        - create a variable that
            - gets your earnings per second based on your hourly wage

        - create variables that initialize default values
            - current earnings at 0
            - seconds elapsed at 0
            - remaining seconds set to however long is left on the shift seconds variable created earlier
            - false value for being on break (create a variable called isOnBreak for this) 

        - initialize the stoptrackerbutton.disabled as false

        - create a setInterval to update the countdown timer that occurs every second and assign it to the variable for the countdown, within that interval, do the following:

            - create an if statement that checks if reamining seconds is more than 0
                - decrement remaining seconds
                - turn the remaining seconds into minutes, hours and seconds by creating variables (use Math.floor))
                    - hours: reamining seconds variable / 3600
                    - minutes: (remaining seconds variable modulus 3600) / 60
                    - seconds: remaining seconds modulus 60
                - change the text content of the timer display (variable created earlier) (use toString and padStart methods)

                OPTIONAL - Create a console log to check it is updating every seconds, because your browser may take a few seconds to update

            - add an else statement to the end that clears the countdown interval
            
        - create a setInterval to update the earnings tracker that occurs every second and assign it to the variable for the earnings, within that interval, do the following:

            - create an if statement that checks if seconds elapsed is less than shift seconds

                - CHECK IF ON BREAK - create another if statement that checks if the seconds elapsed is more than or equal to the break start seconds AND if the seconds elapsed is less than break end seconds 
                    - set isOnBreak to true, otherwise set it to false

                - CHECK IF NOT ON BREAK - create another if statement that checks if isOnBreak is false
                    - set current earnings to current earnings plus earnings per second
                    - change the text content of the earnings display (using interpolation) to display current earnings with a toFixed of 2

                - increment seconds elapsed by 1

            - otherwise clear the earnings interval and set the stoptrackerbutton.disabled to true

----------------------------------------------------------------------------------------------------------------

    
    