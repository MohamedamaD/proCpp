# proCpp
thisMyProject
#include <iostream>
#include<string>
using namespace std;
struct date {

	int day;

	int mounth;

	int year;

};
struct travel {

	string nameoftravel;

	int numberoftravel;

	int number_seats;//عدد المقاعد 

	int avalable_Seats;//عدد المقاعد المتاحه

	int number_of_trip; //رقم الرحله

	date dateoftravel;//تاريخ الرحله

	//ملعومات المغادره
	string From_city;//المدينه الي هتغادر منها

	float depture_time;//معاد المغادره

	//ملعومات الوصول
	string to_city;//المدينه بتاعت الوصول

	float arrival_date;//معاد الوصول

};
struct traveler
{
	string name[4];

	int PhoneNumber;

	string address[2];

	string Nationality;

	long long ID;

	int numberofbook;

};
struct ticket {

	int noticket;

	traveler informationformtraveler;

	travel informationformaltraver;

	date dateofbook;

};

void set_name_of_traveler(traveler& object);

void get_name_of_traveler(traveler& object);

void set_PhoneNumber(traveler& object);

int get_PhoneNumber(traveler& object);

void set_address(traveler& object);

string get_address(traveler& object);
 
void set_Nationality(traveler& object);

string get_Nationality(traveler& object);

void set_id(traveler& object);

long long get_id(traveler& object);

void set_nameoftravel(travel& obj);

string get_nameoftravel(travel& obj);

void set_numberoftravel(travel& obj);

int get_numberoftravel(travel& obj);

void add_travell(travel& obj);

void get_travell(travel& obj);

void set_number_seats(travel& obj);

int get_number_seats(travel& obj);

void set_avalable_Seats(travel& obj);

int get_avalable_Seats(travel& obj);

void set_number_of_plane(travel& obj);

int get_number_of_plane(travel& obj);

void set_date_travel(travel& obj);

void get_date_travel(travel& obj);

void set_from_city(travel& obj);

string get_from_city(travel& obj);

void set_to_city(travel& obj);

string get_to_city(travel& obj);

void set_depture_time(travel& obj);

float get_depture_time(travel& obj);

void set_arrival_date(travel& obj);

float get_arrival_date(travel& obj);

void menu();

void add_mosafer(traveler& object);

void add_reservation(travel obj[]);

void  Search_available_flights(travel obj[]);

void Show_booking_history(ticket object[]);

void edit_book(ticket object[]);

void menu1();

void menu2();

void del_travell(travel obj[],int x);// هنعملها بال gui وهنمسحها من قدامو 

void cheak_idd(traveler obj[], long long va);

void ref_travell(travel& obj);//نفس الكلام عشان نعملو زراير يغير الي عايزو براحتو 

int  i = 0 ;//counter of travel 

int counter_for_num_of_add_travel = 0;//بيعد كام مرا اتعمل حجز

int k = 0;//counter of traveler



int q = 0;//counter of ticket

long long cheak_id_for_unchange;//بيدخل فيه القيمه الي بنعمل تشك عليها لل اي دي

int main() {

	//رقم الي هيختارو 
	int numberofchocie;

	//عدد الرحلات
	travel one[1000];


	bool flag = true;
	bool search = false;


	//عدد المسافرين
	traveler two[1000];
	
	//مستخدم ف case5هو فلاج بنسبه لل id 
	bool cheak1 = false;

	//عدد التذاكر
	ticket tecket[1000];
	
	bool cheek7 = false;
	bool cheek8 = false;
	bool final = false;
	string chek;
	
	//sign
	bool close1 = true;



	


	cout << "\n\n\n\t\t\t\t**Welcome to the flight reservation system**\n\n\n";
	
	for (i = 0; flag; ) {

		bool esc1 = true;

		bool esc2 = true;

		cout << "\n\n\n\t\t\t If you are an Admin press 1 if you are a Customer press 2 ...\n\n";

		int chosenNumber;

		cin >> chosenNumber;//رقم الادم او العميل

		string x;

		switch (chosenNumber) {
		case 1:

			cout << "\n **Please enter the password**\n";
		
			cin >> x;

			if (x == "Egymaster@111")
			{
				cout << "\n Welcome Admin \n\n";

			}
			else {
				cout << "\n The password is wrong \n\n";
				break;
			}

			

			

			while (esc1)
			{

				menu1();

				cout << " \n Enter the number you want to do :\n";

				int numberofchocie1;

				cin >> numberofchocie1;

				switch (numberofchocie1)
				{
				case 1:

					add_travell(one[i]);

					i++;

					counter_for_num_of_add_travel++;

					break;

				case 2:
					if (i != 0)
					{


						cout << " Enter the flight number you want to delete it : \n";

						Search_available_flights(one);

						//رقم الرحله الي هيخش
						int count10;

						cin >> count10;

						del_travell(one, count10);
					}
					else
					{
						cout << " \n There are no flights : \n";
					}
					break;

				case 3:
					if (i != 0)
					{

						cout << " Enter the flight number you want to modify : \n";

						Search_available_flights(one);

						//رقم الرحله الي هتتعدل
						int answer1;

						cin >> answer1;

						for (int z = 0; z < i; z++)
						{
							if (one[z].numberoftravel == answer1)
							{
								ref_travell(one[z]);
							}
						}
					}
					else
					{
						cout << " \n There are no flights : \n";
					}
					break;

				case 4:
					if (i != 0)
					{
						Search_available_flights(one);
					}
					else
					{
						cout << "\n There are no reservations or tickets in the system : \n";
					}
					break;
				case 5:

					esc1 = false;

					break;
				}
			}
			break;
		case 2:
			while (esc2)
			{

				cout << "\n **Please chose what you want to do**\n";

				menu2();

				int numberofchoice2;

				cin >> numberofchoice2;

				switch (numberofchoice2) {

				case 1:

					if (i != 0)
					{

						cout << " Enter your ID please : \n";

						//هيشيل ال اي دي الي داخل
						long long cheak_id;

						//عشان نبقا عارفين مكانو فين ف الاراي 
						int index_cheaked;

						cin >> cheak_id;

						for (int b = 0; b < k; b++)
						{
							if (cheak_id == two[b].ID)
							{
								//flag
								cheak1 = true;

								index_cheaked = b;
							}
						}
						if (cheak1) {

							cout << " You are registered in the system, please choose the appropriate flight for you : \n";

							Search_available_flights(one);

							add_reservation(one);

							cout << " Enter the name of travell : \n";

							string ansewr_1;

							cin >> ansewr_1;

							int t;

							for (int e = 0; e < i; e++)
							{
								if (ansewr_1 == one[e].nameoftravel)
								{
									tecket[q].informationformaltraver.From_city = one[e].From_city;

									tecket[q].informationformaltraver.to_city = one[e].to_city;

									tecket[q].informationformaltraver.depture_time = one[e].depture_time;

									tecket[q].informationformaltraver.arrival_date = one[e].arrival_date;

									tecket[q].informationformaltraver.nameoftravel = one[e].nameoftravel;

									t = e;
								}
							}

							one[t].avalable_Seats -= 1;

							tecket[q].noticket = (q + 1);

							tecket[q].informationformtraveler.ID = cheak_id;

							for (int size = 0; size < 4; size++)
							{
								tecket[q].informationformtraveler.name[size] = two[index_cheaked].name[size];
							}

							q++;

							cheak1 = false;//هيرجع لقيمتو ب انتهاء ال case


						}
						else
						{
							cout << " Sorry, you are not registered in the system, please register and try again : \n";
						}
					}
					else
					{
						cout << " \n There are no flights currently available : \n";
					}
					break;
				case 2:
					add_mosafer(two[k]);

					cheak_id_for_unchange = two[k].ID;


					cheak_idd(two, cheak_id_for_unchange);

					cheak_idd(two, cheak_id_for_unchange);

					cheak_idd(two, cheak_id_for_unchange);

					k++;

					break;
				case 3:
					if (i != 0 && k != 0)
					{

						cout << " enter your id : \n";

						//هيشيل الاندكس بردو والقيمه بتاعت الاي دي
						int idofdel, indexofdel;

						cin >> idofdel;

						for (int m = 0; m < q; m++)
						{
							if (idofdel == tecket[m].informationformtraveler.ID)
							{
								indexofdel = m;

								cout << " Number of ticket : " << tecket[m].noticket << endl;

								cout << " Name Of Travell : " << tecket[m].informationformaltraver.nameoftravel << endl;

								cout << " The name of the ticket owner : " << tecket[m].informationformtraveler.name[0] << " " <<

									tecket[m].informationformtraveler.name[1] << " " << tecket[m].informationformtraveler.name[2] << " " <<

									tecket[m].informationformtraveler.name[3] << " " << " The ID of the ticket onwer : " << tecket[m].informationformtraveler.ID << endl;

								cout << " The plane will depart from : " << tecket[m].informationformaltraver.From_city << " The plane will land in : " << tecket[m].informationformaltraver.to_city << endl;

								cout << " Flight departure time : " << tecket[m].informationformaltraver.depture_time << " Flight arrival time : " << tecket[m].informationformaltraver.arrival_date << endl;

								final = true;
							}
						}
						if (final)
						{
							cout << " enter name of aly 3ayzha delete :\n";

							string p;

							cin >> p;

							for (int u = 0; u < q; u++)
							{
								if (p == tecket[u].informationformaltraver.nameoftravel)
								{
									tecket[u].noticket = 0;

									tecket[u].informationformaltraver.nameoftravel = " None";

									tecket[u].informationformtraveler.name[0] = " None";

									tecket[u].informationformtraveler.name[1] = " None";

									tecket[u].informationformtraveler.name[2] = " None";

									tecket[u].informationformtraveler.name[3] = " None";

									tecket[u].informationformtraveler.ID = 0;

									tecket[u].informationformaltraver.From_city = " None";

									tecket[u].informationformaltraver.to_city = " None";

									tecket[u].informationformaltraver.depture_time = 0;

									tecket[u].informationformaltraver.arrival_date = 0;

									cout << "**Done**\n";
								}
								final = false;
							}
						}
						if (final == false)
						{
							cout << " id is invalid :\n";
						}
					}
					else
					{
						cout << " \n There are no flights booked :\n ";
					}
					break;
				case 4:
					if (i != 0 && k != 0)
					{

						cout << " your ID :\n";

						int idche, indexofid;

						cin >> idche;

						for (int d = 0; d < k; d++)
						{
							if (idche == two[d].ID)
							{
								cheek7 = true;

								indexofid = d;
							}
						}

						Show_booking_history(tecket);

						cout << " Enter name of travell :\n";

						for (int m = 0; m < q; m++)
						{

							if (tecket[m].informationformtraveler.ID == idche)
							{

								cout << " Number of ticket : " << tecket[m].noticket << endl;

								cout << " Name Of Travell : " << tecket[m].informationformaltraver.nameoftravel << endl;

								cout << " The name of the ticket owner : " << tecket[m].informationformtraveler.name[0] << " " <<

									tecket[m].informationformtraveler.name[1] << " " << tecket[m].informationformtraveler.name[2] << " " <<

									tecket[m].informationformtraveler.name[3] << " " << " The ID of the ticket onwer : " << tecket[m].informationformtraveler.ID << endl;

								cout << " The plane will depart from : " << tecket[m].informationformaltraver.From_city << " The plane will land in : " << tecket[m].informationformaltraver.to_city << endl;

								cout << " Flight departure time : " << tecket[m].informationformaltraver.depture_time << " Flight arrival time : " << tecket[m].informationformaltraver.arrival_date << endl;
							}
						}


						int index7;


						cin >> chek;

						for (int s = 0; s < q; s++)
						{
							if (chek == tecket[s].informationformaltraver.nameoftravel)
							{
								index7 = s;

								cheek8 = true;

							}
						}
						if (cheek8)
						{

							if (cheek7)
							{
								cout << "** the avilabel travell **\n\n";

								Search_available_flights(one);

								cout << " Choice number of  new travell : \n";

								int var;

								cin >> var;

								for (int f = 0; f < i; f++)
								{
									if (var == one[f].numberoftravel)
									{
										tecket[index7].informationformaltraver.From_city = one[f].From_city;

										tecket[index7].informationformaltraver.to_city = one[f].to_city;

										tecket[index7].informationformaltraver.depture_time = one[f].depture_time;

										tecket[index7].informationformaltraver.arrival_date = one[f].arrival_date;

										tecket[index7].informationformaltraver.nameoftravel = one[f].nameoftravel;

									}
								}
								cout << " **Done** \n";
							}
							else
							{
								cout << " The id of traveler is not exist Please try agine :\n";
							}
						}
						else
						{
							cout << " The ticket is not exist Please try agine :\n";
						}
					}
					else
						{
						cout << " \n There are no flights booked :\n ";
						}
					break;
				case 5:
					if (q != 0)
					{
						Show_booking_history(tecket);
					}
					else
					{
						cout << " There are no reservations or tickets in the system : \n";
					}
					break;
				case 6:

					esc2 = false;

					break;

					/*default:
						cout << " Enter the number from 1 to 9 :\n";
						break;*/
				}
			}
		}







	



























		//bool flagge = false;

		//cout << " Enter the number you want to do :\n";

		//menu();

		//cin >> numberofchocie;

		//switch (numberofchocie)
		//{
		//case 1:
		//	add_travell(one[i]);

		//	i++;

		//	counter_for_num_of_add_travel++;

		//	break;
		//case 2:

		//	cout << " Enter the flight number you want to delete it : \n";

		//	Search_available_flights(one);

		//	//رقم الرحله الي هيخش
		//	int count10;

		//	cin >> count10;

		//	del_travell(one, count10);
		//	
		//	break;
		//case 3:
		//	cout << " Enter the flight number you want to modify : \n";

		//	Search_available_flights(one);

		//	//رقم الرحله الي هتتعدل
		//	int answer1;

		//	cin >> answer1;

		//	for (int z = 0; z < i; z++)
		//	{
		//		if (one[z].numberoftravel == answer1)
		//		{
		//			ref_travell(one[z]);
		//		}
		//	}
		//	break;
		//case 4:

		//	Search_available_flights(one);

		//	break;

		//case 5:

		//	cout << " Enter your ID please : \n";

		//	//هيشيل ال اي دي الي داخل
		//	long long cheak_id;

		//	//عشان نبقا عارفين مكانو فين ف الاراي 
		//	int index_cheaked;

		//	cin >> cheak_id;

		//	for (int b = 0; b < k; b++) 
		//	{
		//		if (cheak_id == two[b].ID)
		//		{
		//			//flag
		//			cheak1 = true;		
		//			
		//			index_cheaked = b;
		//		}
		//	}
		//	if (cheak1) {

		//		cout << " You are registered in the system, please choose the appropriate flight for you : \n";

		//		Search_available_flights(one);

		//		add_reservation(one);

		//		cout << " Enter the name of travell : \n";

		//		string ansewr_1;

		//		cin >> ansewr_1;

		//		int t;
		//		
		//		for (int e = 0; e < i; e++)
		//		{
		//			if (ansewr_1==one[e].nameoftravel)
		//			{
		//				tecket[q].informationformaltraver.From_city = one[e].From_city;

		//				tecket[q].informationformaltraver.to_city = one[e].to_city;

		//				tecket[q].informationformaltraver.depture_time = one[e].depture_time;

		//				tecket[q].informationformaltraver.arrival_date = one[e].arrival_date;

		//				tecket[q].informationformaltraver.nameoftravel = one[e].nameoftravel;

		//				
		//			}
		//		}

		//		tecket[q].noticket = (q + 1);

		//		tecket[q].informationformtraveler.ID = cheak_id;

		//		for (int size = 0; size < 4; size++)
		//		{
		//			tecket[q].informationformtraveler.name[size] = two[index_cheaked].name[size];
		//		}
		//		
		//		q++;

		//		cheak1 = false;//هيرجع لقيمتو ب انتهاء ال case

		//		
		//	}
		//	else
		//	{
		//		cout << " Sorry, you are not registered in the system, please register and try again : \n";
		//	}

		//	break;
		//case 6:
		//	cout << " enter your id : \n";
		//	//هيشيل الاندكس بردو والقيمه بتاعت الاي دي
		//	int idofdel,indexofdel;

		//	cin >> idofdel;

		//	for (int m = 0; m < q; m++)
		//	{
		//		if (idofdel==tecket[m].informationformtraveler.ID)
		//		{
		//			indexofdel = m;

		//			cout << " Number of ticket : " << tecket[m].noticket << endl;

		//			cout << " Name Of Travell : " << tecket[m].informationformaltraver.nameoftravel << endl;

		//			cout << " The name of the ticket owner : " << tecket[m].informationformtraveler.name[0] << " " <<

		//			tecket[m].informationformtraveler.name[1] << " " << tecket[m].informationformtraveler.name[2] << " " <<

		//			tecket[m].informationformtraveler.name[3] << " " << " The ID of the ticket onwer : " << tecket[m].informationformtraveler.ID << endl;

		//			cout << " The plane will depart from : " << tecket[m].informationformaltraver.From_city << " The plane will land in : " << tecket[m].informationformaltraver.to_city << endl;

		//			cout << " Flight departure time : " << tecket[m].informationformaltraver.depture_time << " Flight arrival time : " << tecket[m].informationformaltraver.arrival_date << endl;

		//			final = true;
		//		}
		//	}
		//	if (final)
		//	{
		//		cout << " enter name of aly 3ayzha delete :\n";

		//		string p;

		//		cin >> p;

		//		for (int u = 0; u < q; u++)
		//		{
		//			if (p==tecket[u].informationformaltraver.nameoftravel)
		//			{
		//				tecket[u].noticket = 0;

		//				tecket[u].informationformaltraver.nameoftravel = " None";

		//				tecket[u].informationformtraveler.name[0] = " None";

		//				tecket[u].informationformtraveler.name[1] = " None";

		//				tecket[u].informationformtraveler.name[2] = " None";

		//				tecket[u].informationformtraveler.name[3] = " None";

		//				tecket[u].informationformtraveler.ID = 0;

		//				tecket[u].informationformaltraver.From_city = " None";

		//				tecket[u].informationformaltraver.to_city= " None";

		//				tecket[u].informationformaltraver.depture_time = 0;

		//				tecket[u].informationformaltraver.arrival_date = 0;

		//				cout << "**Done**\n";
		//			}
		//			final = false;
		//		}
		//	}
		//	if (final==false)
		//	{
		//		cout << " id is invalid :\n";
		//	}
		//	break;
		//case 7:

		//	cout << " your ID :\n";

		//	int idche,indexofid;
		//	
		//	cin >> idche;

		//	for (int  d = 0; d < k; d++)
		//	{
		//		if (idche==two[d].ID)
		//		{
		//			cheek7 = true;

		//			indexofid = d;
		//		}
		//	}
		//	
		//	cout << " Enter name of travell :\n";

		//	Show_booking_history(tecket);

		//	for (int m = 0; m < q; m++)
		//	{
		//		
		//		if (tecket[m].informationformtraveler.ID==idche)
		//		{

		//			cout << " Number of ticket : " << tecket[m].noticket << endl;

		//			cout << " Name Of Travell : " << tecket[m].informationformaltraver.nameoftravel << endl;

		//			cout << " The name of the ticket owner : " << tecket[m].informationformtraveler.name[0] << " " <<

		//			tecket[m].informationformtraveler.name[1] << " " << tecket[m].informationformtraveler.name[2] << " " <<

		//			tecket[m].informationformtraveler.name[3] << " " << " The ID of the ticket onwer : " << tecket[m].informationformtraveler.ID << endl;

		//			cout << " The plane will depart from : " << tecket[m].informationformaltraver.From_city << " The plane will land in : " << tecket[m].informationformaltraver.to_city << endl;

		//			cout << " Flight departure time : " << tecket[m].informationformaltraver.depture_time << " Flight arrival time : " << tecket[m].informationformaltraver.arrival_date << endl;
		//		}
		//	}
		//	

		//	int index7;


		//	cin >> chek;

		//	for (int s = 0; s < q; s++)
		//	{
		//		if (chek==tecket[s].informationformaltraver.nameoftravel)
		//		{
		//			index7 = s;

		//			cheek8 = true;

		//		}
		//	}
		//	if (cheek8)
		//	{

		//		if (cheek7)
		//		{
		//			cout << "** the avilabel travell **\n\n";

		//			Search_available_flights(one);

		//			cout << " Choice number of  new travell : \n";

		//			int var;

		//			cin >> var;

		//			for (int f = 0; f < i; f++)
		//			{
		//				if (var == one[f].numberoftravel)
		//				{
		//					tecket[index7].informationformaltraver.From_city = one[f].From_city;

		//					tecket[index7].informationformaltraver.to_city = one[f].to_city;

		//					tecket[index7].informationformaltraver.depture_time = one[f].depture_time;

		//					tecket[index7].informationformaltraver.arrival_date = one[f].arrival_date;

		//					tecket[index7].informationformaltraver.nameoftravel = one[f].nameoftravel;

		//				}
		//			}
		//			cout << " **Done** \n";
		//		}
		//		else
		//		{
		//			cout << " The id of traveler is not exist Please try agine :\n";
		//		}
		//	}
		//	else
		//	{
		//		cout << " The ticket is not exist Please try agine :\n";
		//	}
		//	
		//	break;
		//case 8:
		//	if (q!=0)
		//	{
		//		Show_booking_history(tecket);
		//	}
		//	else
		//	{
		//		cout << " There are no reservations or tickets in the system : \n";
		//	}
		//	

		//	break;
		//case 9:
		//		add_mosafer(two[k]);
		//	
		//	 cheak_id_for_unchange = two[k].ID;


		//	 cheak_idd(two, cheak_id_for_unchange);

		//	 cheak_idd(two, cheak_id_for_unchange);

		//	 cheak_idd(two, cheak_id_for_unchange);

	

		//	 k++;
		//	
		//	break;

		//default:
		//	cout << " Enter the number from 1 to 9 :\n";
		//	break;
		//}



		
	}
	return 0;
}


void set_nameoftravel(travel& obj)
{
	cout << " Enter name of travel :\n\n";

	cin >> obj.nameoftravel;
}

string get_nameoftravel(travel& obj)
{
	return obj.nameoftravel;
}

void set_numberoftravel(travel& obj)
{
	cout << " Enter number of travel :\n\n";
	cin >> obj.numberoftravel;
}

int get_numberoftravel(travel& obj)
{
	return obj.numberoftravel;
}

void add_travell(travel& obj)
{
	set_nameoftravel(obj);

	set_numberoftravel(obj);

	set_number_seats(obj);

	set_avalable_Seats(obj);

	set_number_of_plane(obj);

	set_date_travel(obj);

	set_from_city(obj);

	set_to_city(obj);

	set_depture_time(obj);

	set_arrival_date(obj);
}

void get_travell(travel& obj)
{
	cout << " The name of travel is : " << get_nameoftravel(obj) << "\n The number of travel is : " << get_numberoftravel(obj);

	cout << "\n The number seats is : " << get_number_seats(obj) << "\n The avalable Seats is : " << get_avalable_Seats(obj);

	cout << "\n The number of trip is : " << get_number_of_plane(obj) << "\n The date of travel is :" ;

	get_date_travel(obj);

	cout << "\n The plane takes off from : " << get_from_city(obj) << "\n The plane is landing : " << get_to_city(obj) << endl;

	cout << " The plane takes off at the clock : " << get_depture_time(obj) << " The plane lands at the clock : " << get_arrival_date(obj)<<endl;
}

void set_number_seats(travel& obj) {
	cout << " Enter the number of seats \n\n";
	cin >> obj.number_seats;
}

int get_number_seats(travel& obj) {
	return obj.number_seats;
}

void set_avalable_Seats(travel& obj) {
	cout << " Enter the number of available seats \n\n";
	cin >> obj.avalable_Seats;
}

int get_avalable_Seats(travel& obj) {
	return obj.avalable_Seats;
}

void set_number_of_plane(travel& obj) {
	cout << " Enter the flight number \n\n";
	cin >> obj.number_of_trip;
}

int get_number_of_plane(travel& obj) {
	return obj.number_of_trip;
}

void set_date_travel(travel& obj) {

	cout << " Enter date of travel :\n\n";

	cout << " DaY: ";

	cin >> obj.dateoftravel.day;

	cout << " Mounth :";

	cin >> obj.dateoftravel.mounth;

	cout << " Year :";

	cin>> obj.dateoftravel.year;
}

void get_date_travel(travel& obj) {
	cout<< obj.dateoftravel.day <<" / "<< obj.dateoftravel.mounth << " / " << obj.dateoftravel.year;
}

void set_from_city(travel& obj) {
	cout << " Enter the exit location of the plane \n\n";
	string x;//هخزن في المدينه عشان لو هعدل عليها مش اعدل علي الاصل لاول
	cin >> x;
	obj.From_city = x;
}

string get_from_city(travel& obj) {
	return obj.From_city;
}

void set_to_city(travel& obj) {
	cout << " Enter the place of arrival of the plane \n\n";
	string a;
	cin >> a;
	obj.to_city = a;
}

string get_to_city(travel& obj) {
	return obj.to_city;
}

void set_depture_time(travel& obj) {
	cout << " Enter the flight departure time \n\n";
	cin >> obj.depture_time;
}

float get_depture_time(travel& obj) {
	return  obj.depture_time;
}

void set_arrival_date(travel& obj) {
cout << " Enter the arrival time of the plane \n\n";
	cin >> obj.arrival_date;
}

float get_arrival_date(travel& obj) {
	return  obj.arrival_date;
}
void menu() {
	cout << " \n1 : Add a new flight schedule :\n 2 : Delete the current flight schedule :\n 3 : Update the current flight schedule :\n 4 : Search available flights :\n 5 : add reservation :\n 6 : cancel reservation :\n 7 : Edit reservation :\n 8 : Show booking history :\n 9 : sign in :\n" ;
}

void add_mosafer(traveler& object)
{
	set_name_of_traveler(object);

	set_Nationality(object);

	set_id(object);	

	set_PhoneNumber(object);

	set_address(object);

	cout << " ** Your information is complete congratulation **\n";
}

void add_reservation(travel obj[])
{
	cout << " Enter the flight number you want to book : \n";

	bool cheaked = false;

	int numb;
	
	cin >> numb;

	

	for (int d = 0; d < k; d++)
	{
		if (obj[d].numberoftravel == numb)
		{
			cheaked = true;
		}
	}

	if (cheaked)
	{
		cout << " The flight has been booked :\n";

	}
	else
	{
		cout << " invalid number \n";
	}


}

void Search_available_flights(travel obj[])
{
	
	if (counter_for_num_of_add_travel > 0)
	{
		cout << " The available flights : \n";

		for (int m = 0; m < counter_for_num_of_add_travel; m++)
		{
			if (obj[m].numberoftravel != 0)
			{
				cout << " Travell number : " << obj[m].numberoftravel << endl;

				get_travell(obj[m]);
			}
			
		}
	}
	else
	{
		cout << " The flights is not available : \n";
	}
}

void Show_booking_history(ticket object[])
{
	for (int x = 0; x < q; x++)
	{
		cout << " Number of ticket : " << object[x].noticket << endl << endl;

		cout << " Name Of Travell : " << object[x].informationformaltraver.nameoftravel << endl << endl;

		cout << " The name of the ticket owner : " << object[x].informationformtraveler.name[0] << " " << 

		object[x].informationformtraveler.name[1] << " " <<object[x].informationformtraveler.name[2] << " " <<
			
		object[x].informationformtraveler.name[3] << " " << " The ID of the ticket onwer : " << object[x].informationformtraveler.ID << endl << endl;

		cout << " The plane will depart from : " << object[x].informationformaltraver.From_city << " The plane will land in : " << object[x].informationformaltraver.to_city << endl << endl;

		cout << " Flight departure time : " << object[x].informationformaltraver.depture_time << " Flight arrival time : " << object[x].informationformaltraver.arrival_date << endl << endl;
	}
}

void edit_book(ticket object[])
{

}

void del_travell(travel obj[],int x) {

		bool flagge = false;

	for (int l = 0; l < i; l++)
	{

		if (obj[l].numberoftravel == x)
		{

			 flagge = true;

			obj[l].nameoftravel = "none";

			obj[l].numberoftravel = 0;

			obj[l].number_seats = 0;

			obj[l].avalable_Seats = 0;

			obj[l].number_of_trip = 0;

			obj[l].From_city = "none";

			obj[l].to_city = "none";

			obj[l].dateoftravel.day = 0;

			obj[l].dateoftravel.mounth = 0;

			obj[l].dateoftravel.year = 0;

			obj[l].depture_time = 0;

			obj[l].arrival_date = 0;

		}

	}
	if (flagge)
	{
		cout << " The travell is deleted : \n";
	}
	else
	{
		cout << " The travell is not exist : \n";
	}

}

void ref_travell(travel& obj)
{
	bool flage = true;
	
	while (flage)
	{
		cout << "Enter the number of the thing you want to modify : \n";

		cout << " 1 : Name of travel : \n 2 : Number of travel : \n 3 : Number of seats : \n 4 : Avalibal seats : \n 5 : Number of trip : \n 6 : Form city : \n 7 : Depture time : \n 8 : To city : \n 9 : Arrival date : \n 10 : date of travel : \n";
		int index;
		cin >> index;

		switch (index)
		{
		case 1:
			set_nameoftravel(obj);
			break;
		case 2:
			set_numberoftravel(obj);
			break;
		case 3:
			set_number_seats(obj);
			break;
		case 4:
			set_avalable_Seats(obj);
			break;
		case 5:
			set_number_of_plane(obj);
			break;
		case 6:
			set_from_city(obj);
			break;
		case 7:
			set_depture_time(obj);
			break;
		case 8:
			set_to_city(obj);
			break;
		case 9:
			set_arrival_date(obj);
			break;
		case 10:
			set_date_travel(obj);
			break;
		default:
			break;
		}
		cout << " Do you want to modify something else ? (yes or no)\n";
		string x;
		cin >> x;
		if (x == "no" || x == "No" || x == "NO") {
			flage = false;
		}


	}
}

void set_name_of_traveler(traveler& object)
{
	cout << " Enter first name : ";
	cin >> object.name[0];
	cout << " Second : ";
	cin >> object.name[1];
	cout << " Third : ";
	cin >> object.name[2];
	cout << " fourth  : ";
	cin >> object.name[3];

}

void get_name_of_traveler(traveler& object)
{
	cout << " Your name is : " << object.name[0] << " / " << object.name[1] << " / " << object.name[2] << " / " << object.name[3] << endl;
}

void set_PhoneNumber(traveler& object)
{
	cout << " Enter your phonenumber : \n";
	cin >> object.PhoneNumber;
}

int get_PhoneNumber(traveler& object)
{
	return object.PhoneNumber;
}

void set_address(traveler& object)
{
	cout << "please enter your Adress : \n"<<" Country : ";

	cin >> object.address[0];

	cout << " Governorate : ";

	cin >> object.address[1];  
	
} 

string get_address(traveler& object)
{
	return object.address[0];
	return object.address[1];
}

void set_Nationality(traveler& object)
{
	cout << " What your Nationality : \n";
	cin >> object.Nationality;
}

string get_Nationality(traveler& object)
{
	return object.Nationality;
}

void set_id(traveler& object)
{
	cout << " What is your id : \n";
	cin >> object.ID;
}

long long get_id(traveler& object)
{
	return object.ID;
	
}
void cheak_idd(traveler obj[], long long va) {

	for (int e = 0; e < k; e++)
	{
		if (obj[e].ID == va)
		{

			cout << " This ID is exist ,Please enter one else \n What is the true ID : \n";

			cin >> obj[k].ID;

		}

	}

}
void menu1() {
	cout << "\n 1 : Add a new flight schedule :\n\n 2 : Delete the current flight schedule :\n\n 3 : Update the current flight schedule :\n\n 4 : Search available flights :\n\n 5 : Exit from System : \n";
}
void menu2() {
	cout << "\n 1 : Add reservation :\n\n 2 : Sign in :\n\n 3 : Cancel reservation :\n\n 4 : Edit reservation :\n\n 5 : How booking history : \n\n 6 : Exit : \n";
}
