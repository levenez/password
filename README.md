# password
Condition d'un mot de passe valide
<?php

// Un mot de passe est valide si:
//      - au moins 8 caractères
//      - au moins 1 majuscule et 1 minuscule
//      - au moins un chiffre

function hasMajuscule($password){
    for ($i=0; $i < strlen($password); $i++) { 
        if (!is_numeric($password[$i]) AND $password[$i] === strtoupper($password[$i])){
            return true;
        }
    }
    return false;
}


function hasMinuscule($password){
    for ($i = 0; $i < strlen($password); $i++){
        if ($password[$i] === strtolower($password[$i])){
            return true;
        }
    }
    return false;
}

function hasNumber($password){
    foreach(str_split($password) as $char){
        if (is_numeric($char))
            return true;
    }
    return false;
}





function checkPasswordStrongness($password){
    return strlen($password) >= 8 AND hasMinuscule($password) 
    AND hasMajuscule($password) AND hasNumber($password);

}

var_dump(checkPasswordStrongness("unPassword56"));
