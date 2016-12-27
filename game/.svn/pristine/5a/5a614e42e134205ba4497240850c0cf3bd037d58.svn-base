using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Events;
using System.Collections.Generic;


public enum MessageType { Success,Warning,Error }

public class LoginManager : MonoBehaviour {

    public UnityEvent OnLogin, OnLogout;

    // Page Create
    public GameObject username;
    public GameObject email;
    public GameObject password;
    public GameObject confPassword;
    public Button buttonCreate;

    private string Username;
    private string Email;
    private string Password;
    private string ConfPassword;
    private string form;
    private bool EmailValid = false;
    private Button btnCreate;

    // Page Login
    public GameObject user;
    public GameObject passwordLogin;
    public Button buttonLogin;
    public Button buttonGoToPageCreate;

    private string User;
    private string PasswordLogin;
    private Button btnLogin;
    private Button btnGoToPageCreate;

    // Page Logged
    public GameObject helloText;

    //private string HelloText;

    // Pages
    public GameObject pageCreate;
    public GameObject pageLogin;
    public GameObject pageLogged;

    private bool isShowingPageCreate;
    private bool isShowingPageLogin;
    private bool isShowingPageLogged;

    //private bool isCreateAccountClicked;
    //private bool isCheckAuthenticationClicked;
    //private bool isGoToPageCreateClicked;

    // List of Users
    private List<User> users;
    private User currentUser;


    void Start()
    {
        users = new List<User>();
        isShowingPageCreate = false;
        isShowingPageLogin = true;
        isShowingPageLogged = false;
        pageCreate.SetActive(isShowingPageCreate);
        pageLogin.SetActive(isShowingPageLogin);
        pageLogged.SetActive(isShowingPageLogged);
        
        btnCreate = buttonCreate.GetComponent<Button>();
        btnCreate.onClick.AddListener(CreateAccount);

        btnLogin = buttonLogin.GetComponent<Button>();
        btnLogin.onClick.AddListener(CheckAuthentication);

        btnGoToPageCreate = buttonGoToPageCreate.GetComponent<Button>();
        btnGoToPageCreate.onClick.AddListener(GoToPageCreate);
        
        //HelloText = helloText.GetComponent<InputField>().text;
        //isGoToPageCreateClicked = false;

    }

    void Update()
    {
        //Debug.Log(isShowingPageCreate);
        if (isShowingPageLogin)
        {
            User = user.GetComponent<InputField>().text;
            PasswordLogin = passwordLogin.GetComponent<InputField>().text;

        } else if (isShowingPageCreate)
        {
            Username = username.GetComponent<InputField>().text;
            Email = email.GetComponent<InputField>().text;
            Password = password.GetComponent<InputField>().text;
            ConfPassword = confPassword.GetComponent<InputField>().text;
        }
        else if (isShowingPageLogged)
        {
            
        }
        
    }

    public void GoToPageCreate()
    {
        isShowingPageCreate = !isShowingPageCreate;
        isShowingPageLogin = !isShowingPageLogin;

        pageCreate.SetActive(isShowingPageCreate);
        pageLogin.SetActive(!isShowingPageLogin);
    }
    
    //Here you must put the code to check the authentication for a user
    public void CheckAuthentication()
    {
        bool userFound = false;
        foreach(User u in users)
        {
            if ((u.Login == User) && (u.Password == PasswordLogin))
            {
                currentUser = u;
                Login();
                userFound = true;
            }
        }
        if (!userFound)
        {
            Debug.Log("Login or password incorrect");
        }
    }


    //here you must put the code when the authentication process is valid
    protected void Login()
    {
        isShowingPageLogged = true;
        isShowingPageLogin = false;
        isShowingPageCreate = false;

        pageLogin.SetActive(isShowingPageLogin);
        pageLogged.SetActive(isShowingPageLogged);
        pageCreate.SetActive(isShowingPageCreate);

        Debug.Log("LOGGED");

        helloText.GetComponent<Text>().text = "Bonjour " + currentUser.Login;
    }

    
    //You must put the code for creating an account in this function
    public void CreateAccount()
    {
        if ((Username != null) || (Username != "") && (Email != "") && (Password != "") && (Password == ConfPassword))
        {
            bool userExist = false;
            foreach (User u in users)
            {
                if ((u.Login == Username) || (u.Email == Email))
                {
                    userExist = true;
                    Debug.Log("Account already exist !");
                }
            }
            if (!userExist)
            {
                User user = new User();
                user.Login = Username;
                user.Email = Email;
                user.Password = Password;
                users.Add(user);

                foreach (User u in users)
                {
                    Debug.Log(u.Login);
                    Debug.Log(u.Password);
                }

                Debug.Log("Account successfully created");

                username.GetComponent<InputField>().text = "";
                email.GetComponent<InputField>().text = "";
                password.GetComponent<InputField>().text = "";
                confPassword.GetComponent<InputField>().text = "";

                // Go To login page
                isShowingPageCreate = !isShowingPageCreate;
                isShowingPageLogin = !isShowingPageLogin;

                pageCreate.SetActive(isShowingPageCreate);
                pageLogin.SetActive(isShowingPageLogin);
            }

        }
        else
        {
            Debug.Log("Please enter informations in all the fields");
        }
        
    }

    //You can handle the logout here.
    internal void Logout()
    {
    }
    
    //Facultative: you may send allow an user to get his password back by sending him a mail
    public void RecoverPassword()
    {
    }

    public void ResetPassword()
    {
    }

    

    /// <summary>
    /// ////////END UI
    /// </summary>
}

internal class User
{
    private string email;
    private string login;
    private string password;

    public string Email
    {
        get { return email; }
        set { email = value; }
    }

    public string Login
    {
        get { return login; }
        set { login = value; }
    }

    public string Password
    {
        get { return password; }
        set { password = value; }
    }
}