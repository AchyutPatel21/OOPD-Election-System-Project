# OOPD-Election-System-Project
Programming language  C++
Simple Election System
Design Thinking and Problem Solving Skills

#include<iostream>
using namespace std;

// this names are just for example.
#define candidate1 "Narendra Modi"
#define candidate2 "Rahul Gandhi"
#define candidate3 "Arvind Kejriwal"
#define candidate4 "Mamata Banerjee"


void Admin_login();
void Voter_login();
void castvote();
void votesCount();
void leadingCandidate();


// For Admin login
void Admin_login()
{
    string password;
    int login_attempts =0,choice,UserID;

    while(login_attempts < 5)
    {
        cout<<"\nEnter Your UserID : ";
        cin>>UserID;
       
        if(UserID == 2476)
        {
            cout<<"\n\tName : Admin Name ";
            cout<<"\n\tEnter Password : ";
            cin>>password;
           
            if(password == "password")
            {
                cout<<"\n\tWelcome Admin name."<<endl;
                break;
            }
            
            else
                cout<<"\n\tInvaild Password."<<endl;
        }
       
        else if(UserID == 3420)
        {
            cout<<"\n\tName : Admin name 2 ";
            cout<<"\n\tEnter Password : ";
            cin>>password;
            
            if(password == "password")
            {
                cout<<"\n\tWelcome Admin name 2."<<endl;
                break;
            }
            
            else
                cout<<"\n\tInvaild Password."<<endl;
        }
        
        else
        {
            cout<<"\n\tInvaild UserID."<<endl;
            login_attempts++;
        }   
    }
    
    if(login_attempts == 5)
    {
        cout<<"\n\tToo Many Attempts ! "<<endl;
        exit(1);
        
    }
    
    cout<<"\n\tThank you For Login."<<endl; 
    
    //Options
    cout<<"\n\n1. Find Vote Count";
    cout<<"\n2. Find Leading Candidate";
    cout<<"\n0. Exit";

    cout<<"\n\nEnter Choice : ";
    cin>>choice;

    switch (choice)
    {
        case 1:\
            // for count vote
            votesCount();
            break;
        
        case 2:
            // for see who is leading
            leadingCandidate();
            break;
        
        case 0:
            // for exit
            cout<<"\nExit.";
            exit(1);
        
        default:
            cout<<"\nInvaild Choice.";
            break;
    }
}

// For Voter login
void Voter_login()
{
    char voter_name[50];
    int age;

    cout<<"Enter Voter Name: ";
    cin>>voter_name;
    cout<<"Enter Voter Age: ";
    cin>>age;

    
    if(age>=18)
    {
        // if voter is above 18 than he/she can give a vote.
        // Voter have only one option to give vote
        castvote();
    }
    else
    {
        cout<<"\nYou are not eligibly to give vote.";
    }
}


int voteCount1 = 0, voteCount2 = 0, voteCount3 = 0, voteCount4 = 0, spoiledcount =0;

// Voter Option
void castvote()
{
    int choice;
    
    cout<<"\n\n-----====== Please choose your candidate =====-----";
    cout<<"\n\t1. "<<candidate1;
    cout<<"\n\t2. "<<candidate2;
    cout<<"\n\t3. "<<candidate3;
    cout<<"\n\t4. "<<candidate4;
    cout<<"\n\t5. None of These";

    cout<<"\n\n Input your choice (1 - 4) : ";
    cin>>choice;

    switch (choice)
    {
    
    case 1 :
        voteCount1++;
        cout<<"\n\tYou Voted "<<candidate1;
        break;
    
    case 2 :
        voteCount2++;
        cout<<"\n\tYou Voted "<<candidate2;
        break;
    
    case 3 :
        voteCount3++;
        cout<<"\n\tYou Voted "<<candidate3;
        break;
    
    case 4 : 
        voteCount4++;
        cout<<"\n\tYou Voted "<<candidate4;
        break;
    
    case 5 :
        spoiledcount++;
        cout<<"\n\tYou Voted No Of These.";
        break;
       
    default:
        cout<<"\n----- Wrong Choice !! -----";
        break;
    }
    getchar();

}

// Admin Option no.1
void votesCount()
{
    int Total_Count;
    
    cout<<"\n\n-----===== Voting Statics =====-----";
    cout<<"\n\n\t"<<candidate1<<" - "<<voteCount1;
    cout<<"\n\t"<<candidate2<<" - "<<voteCount2;
    cout<<"\n\t"<<candidate3<<" - "<<voteCount3;
    cout<<"\n\t"<<candidate4<<" - "<<voteCount4;
    cout<<"\n\t Spoiled Votes  "<<spoiledcount;
    
    Total_Count = voteCount1 + voteCount2 + voteCount3 + voteCount4 + spoiledcount;
    
    cout<<"\n\n\tTotal Vote Count - "<<Total_Count;

}

// Admin Option no.2
void leadingCandidate()
{
    cout<<"\n\n-----===== Leading Candidate =====-----";
    
    if(voteCount1 > voteCount2  &&  voteCount1 > voteCount3  &&  voteCount1 > voteCount4)
        cout<<"\n\nLeading Position Candidate name is "<<candidate1<<" with "<<voteCount1<< " Votes.";
    
    else if(voteCount2 > voteCount3  &&  voteCount2 > voteCount4 &&  voteCount2 > voteCount1)
        cout<<"\n\nLeading Position Candidate name is "<<candidate2<<" with "<<voteCount2<< " Votes.";
    
    else if(voteCount3 > voteCount4  &&  voteCount3 > voteCount1  &&  voteCount3 > voteCount2)
        cout<<"\n\nLeading Position Candidate name is "<<candidate3<<" with "<<voteCount3<< " Votes.";
    
    else if(voteCount4 > voteCount1  &&  voteCount4 > voteCount2 &&  voteCount4 > voteCount3)
        cout<<"\n\nLeading Position Candidate name is "<<candidate4<<" with "<<voteCount4<< " Votes.";
    
    else
        cout<<"\n\n----- No - Win Situation -----";   

}

// main function
int main()
{
    int i, choice;
    do
    {
        cout<<"\n\n\n\n\n";
        cout<<("\n\n-----===== Welcome To Election =====-----\n\n");
        cout<<("\n\t1. Admin Login");
        cout<<("\n\t2. Voter Login");
        cout<<("\n\t0. Exit");

        cout<<"\nEnter Choice : ";
        cin>>choice;

        switch (choice)
        {
        case 1 :
            Admin_login();
            break;

        case 2 :
            Voter_login();
            break;

        case 0:
            cout<<"\nExit.";
            exit(1);        
        
        default:
            cout<<"Invaild Choice.";
            break;
        }
    } while (choice !=0);

    getchar();
    return 0;

}
