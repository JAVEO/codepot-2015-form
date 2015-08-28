# codepot-2015-form

demo/index.html

    <form-component>
    </form-component>

Add some inputs: form-component.html

    <template>
	    <div>
          	 <input type="password"
                    id="password"
                    placeholder="Password"
                    autofocus>
        </div>
        <div>
            <input type="password"
                   id="passwordConfirmation"
                   placeholder="Confirm your password">
        </div>
        <button id="submit" on-tap="submitForm">Submit!</button>

        ...
    
    </dom-module>
        <script>
            Polymer({
                is: 'form-component',
                properties: {},
                _submitForm: function(){
                    console.log("submitted!");
                },
        ...
            });
        </script>
        
Get necessary components:
 
    <link rel="import" href="../paper-button/paper-button.html">
    <link rel="import" href="../paper-input/paper-input.html">

Use them:

    <template>
        <div>
            <paper-input type="password"
                   id="password"
                   label="Password"
                   autofocus>
            </paper-input>
        </div>
        <div>
            <paper-input 
                    type="password"
                    id="passwordConfirmation"
                    label="Confirm your password">
             </paper-input>
        </div>
        <paper-button id="submit" 
                      on-click="_submitForm" raised>
                         Submit!
        </paper-button>
    </template>
    
Logic for validation form-component:
    
    ...
    _submitForm: function(){
        var isProperlyConfirmed = this.$.password.value == this.$.passwordConfirmation.value;
        var isPasswordValid = isProperlyConfirmed && !this.$.password.invalid;
        this.$.passwordConfirmation.invalid = !isProperlyConfirmed;

        if(isPasswordValid){
            alert("Succescfully submitted form!")
        } else{
            alert("Something gone wrong :(")
        }
    },
    
    
Parameterize your component:
    
    Polymer({
        is: 'form-component',
        properties: {
            passwordLabel:{
                type: String,
                value: "Password"
            },
            passwordConfirmationLabel: {
                type: String,
                value: "Confirm your password"
            }
        },
