# Airline-Ticket-system
namespace Train {

	using namespace System;
	using namespace System::ComponentModel;
	using namespace System::Collections;
	using namespace System::Windows::Forms;
	using namespace System::Data;
	using namespace System::Drawing;
	using namespace System::IO;

	/// <summary>
	/// Summary for MyForm
	/// </summary>
	public ref class MyForm : public System::Windows::Forms::Form
	{
	public:
		MyForm(void)
		{
			InitializeComponent();
			//
			//TODO: Add the constructor code here
			//
			curr_opt->Text = "Choose..";
			curr_opt->Items->Add("Euro");
			curr_opt->Items->Add("USA");
			curr_opt->Items->Add("Australia");
			curr_opt->Items->Add("Canada");
			curr_opt->Items->Add("Hong Kong");

			
			timer1->Start();
			
			dest_box->Items->Add("New York");
			dest_box->Items->Add("Sydney");
			dest_box->Items->Add("Hong Kong");
			dest_box->Items->Add("Paris");
			dest_box->Items->Add("Toronto");

			
		}

	protected:
		/// <summary>
		/// Clean up any resources being used.
		/// </summary>
		~MyForm()
		{
			if (components)
			{
				delete components;
			}
		}

#pragma endregion

		const double SDfrance = 486153;
		const double Efrance = 504567;
		const double STfrance = 530000;
		const double SDsydney = 68023;
		const double Esydney = 70450;
		const double STsydney = 73500;
		const double SDtoronto = 73986;
		const double Etoronto = 76890;
		const double STtoronto = 78450;
		const double SDhongkong = 27890;
		const double Ehongkong = 28780;
		const double SThongkong = 31678;
		const double SDnewyork = 63485;
		const double Enewyork = 67689;
		const double STnewyork = 69567;

		double Euro;
		double Aus_dollar;
		double USA_dollar;
		double Canada_dollar;
		double Hong_kong_dollar;
	private: System::Void label2_Click(System::Object^ sender, System::EventArgs^ e) {
	}
private: System::Void checkBox1_CheckedChanged(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void label7_Click(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void label8_Click(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void textBox8_TextChanged(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void label9_Click(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void textBox5_TextChanged(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void label3_Click(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void radioButton3_CheckedChanged(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void radioButton2_CheckedChanged(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void label7_Click_1(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void btnCC_Click(System::Object^ sender, System::EventArgs^ e) {
	btnCC->Visible = false;
}
private: System::Void btnCC_open_Click(System::Object^ sender, System::EventArgs^ e) {
	btnCC->Visible = true;
}
private: System::Void MyForm_Load(System::Object^ sender, System::EventArgs^ e) {
	DateTime iDate = DateTime::Now;
	Fdate->Text = iDate.ToShortDateString();
}
private: System::Void curr_opt_SelectedIndexChanged(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void timer1_Tick(System::Object^ sender, System::EventArgs^ e) {
	DateTime iTime = DateTime::Now;
	Ftime->Text = iTime.ToLongTimeString();
}
private: System::Void label12_Click(System::Object^ sender, System::EventArgs^ e) {
}

private: System::Void label22_Click(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void reset_curr_Click(System::Object^ sender, System::EventArgs^ e) {
	curr_1->Text = "";
	curr_2->Text = "";
}
private: System::Void curr_convert_Click(System::Object^ sender, System::EventArgs^ e) {
	USA_dollar = 0.013;
	Euro = 0.011;
	Canada_dollar = 0.017;
	Aus_dollar = 0.018;
	Hong_kong_dollar = 0.10;
	double Indian_rupee = Convert::ToDouble(curr_1->Text);
	if (curr_opt->Text == "Euro") {
		curr_2->Text = "€" + System::Convert::ToString(Indian_rupee * Euro);
	}
	if (curr_opt->Text == "USA") {
		curr_2->Text = "$" + System::Convert::ToString(Indian_rupee * USA_dollar);
	}
	if (curr_opt->Text == "Australia") {
		curr_2->Text = "$" + System::Convert::ToString(Indian_rupee * Aus_dollar);
	}
	if (curr_opt->Text == "Canada") {
		curr_2->Text = "$" + System::Convert::ToString(Indian_rupee * Canada_dollar);
	}
	if (curr_opt->Text == "Hong Kong") {
		curr_2->Text = "$" + System::Convert::ToString(Indian_rupee * Hong_kong_dollar);
	}
}
private: System::Void button1_Click(System::Object^ sender, System::EventArgs^ e) {
	Route_lbl->Text = "Any";
		if(std_btn->Checked && dest_box->Text == "New York" && adt_radio->Checked && sing_radio->Checked){
			class_lbl->Text = "Standard";
			Ticket_lbl->Text = "Single";
			adt_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "New York";
			lblSUB->Text = System::Convert::ToString(SDnewyork);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (std_btn->Checked && dest_box->Text == "New York" && chd_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "Standard";
			Ticket_lbl->Text = "Single";
			chd_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "New York";
			lblSUB->Text = System::Convert::ToString(0.9*SDnewyork);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
			}
		if (bsn_btn->Checked && dest_box->Text == "New York" && adt_radio->Checked && sing_radio->Checked) {
				class_lbl->Text = "Business";
				Ticket_lbl->Text = "Single";
				adt_lbl->Text = "YES";
				from_tag->Text = "Delhi";
				To_tag->Text = "New York";
				Price_tag->Text = "Rs." + System::Convert::ToString(Enewyork);
				Random^ random_1 = gcnew Random;
				int Rand_ref = random_1->Next(25000, 55000);
				ref_lbl->Text = System::Convert::ToString(Rand_ref);
			}
		if (bsn_btn->Checked && dest_box->Text == "New York" && chd_radio->Checked && sing_radio->Checked) {
				class_lbl->Text = "Business";
				Ticket_lbl->Text = "Single";
				chd_lbl->Text = "YES";
				from_tag->Text = "Delhi";
				To_tag->Text = "New York";
				lblSUB->Text = System::Convert::ToString(0.9*Enewyork);
				lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
				lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
				Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
				Random^ random_1 = gcnew Random;
				int Rand_ref = random_1->Next(25000, 55000);
				ref_lbl->Text = System::Convert::ToString(Rand_ref);
			}
			if (first_btn->Checked && dest_box->Text == "New York" && adt_radio->Checked && sing_radio->Checked) {
				class_lbl->Text = "First Class";
				Ticket_lbl->Text = "Single";
				adt_lbl->Text = "YES";
				from_tag->Text = "Delhi";
				To_tag->Text = "New York";
				lblSUB->Text = System::Convert::ToString(STnewyork);
				lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
				lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
				Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
				Random^ random_1 = gcnew Random;
				int Rand_ref = random_1->Next(25000, 55000);
				ref_lbl->Text = System::Convert::ToString(Rand_ref);
			}
			if (first_btn->Checked && dest_box->Text == "New York" && chd_radio->Checked && sing_radio->Checked) {
				class_lbl->Text = "First Class";
				Ticket_lbl->Text = "Single";
				chd_lbl->Text = "YES";
				from_tag->Text = "Delhi";
				To_tag->Text = "New York";
				lblSUB->Text = System::Convert::ToString(0.9 * STnewyork);
				lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
				lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
				Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
				Random^ random_1 = gcnew Random;
				int Rand_ref = random_1->Next(25000, 55000);
				ref_lbl->Text = System::Convert::ToString(Rand_ref);
			}
		
		if (std_btn->Checked && dest_box->Text == "Sydney" && adt_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "Standard";
			Ticket_lbl->Text = "Single";
			adt_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Sydney";
			lblSUB->Text = System::Convert::ToString(SDsydney);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (std_btn->Checked && dest_box->Text == "Sydney" && chd_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "Standard";
			Ticket_lbl->Text = "Single";
			chd_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Sydney";
			lblSUB->Text = System::Convert::ToString(0.9*SDsydney);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (bsn_btn->Checked && dest_box->Text == "Sydney" && adt_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "Business";
			Ticket_lbl->Text = "Single";
			adt_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Sydney";
			lblSUB->Text = System::Convert::ToString(Esydney);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (bsn_btn->Checked && dest_box->Text == "Sydney" && chd_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "Business";
			Ticket_lbl->Text = "Single";
			chd_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Sydney";
			lblSUB->Text = System::Convert::ToString(Esydney*0.9);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (first_btn->Checked && dest_box->Text == "Sydney" && adt_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "First Class";
			Ticket_lbl->Text = "Single";
			adt_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Sydney";
			lblSUB->Text = System::Convert::ToString(STsydney);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (first_btn->Checked && dest_box->Text == "Sydney" && chd_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "First Class";
			Ticket_lbl->Text = "Single";
			chd_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Sydney";
			lblSUB->Text = System::Convert::ToString(STsydney*0.9);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (std_btn->Checked && dest_box->Text == "Toronto" && adt_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "Standard";
			Ticket_lbl->Text = "Single";
			adt_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Toronto";
			lblSUB->Text = System::Convert::ToString(SDtoronto);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (std_btn->Checked && dest_box->Text == "Toronto" && chd_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "Standard";
			Ticket_lbl->Text = "Single";
			chd_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Toronto";
			lblSUB->Text = System::Convert::ToString(SDtoronto*0.9);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (bsn_btn->Checked && dest_box->Text == "Toronto" && adt_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "Business";
			Ticket_lbl->Text = "Single";
			adt_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Toronto";
			lblSUB->Text = System::Convert::ToString(Etoronto);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (bsn_btn->Checked && dest_box->Text == "Toronto" && chd_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "Business";
			Ticket_lbl->Text = "Single";
			chd_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Toronto";
			lblSUB->Text = System::Convert::ToString(Etoronto*0.9);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (first_btn->Checked && dest_box->Text == "Toronto" && adt_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "First Class";
			Ticket_lbl->Text = "Single";
			adt_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Toronto";
			lblSUB->Text = System::Convert::ToString(STtoronto);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (first_btn->Checked && dest_box->Text == "Toronto" && chd_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "First Class";
			Ticket_lbl->Text = "Single";
			chd_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Toronto";
			lblSUB->Text = System::Convert::ToString(0.9*STtoronto);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		
		if (std_btn->Checked && dest_box->Text == "Hong Kong" && adt_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "Standard";
			Ticket_lbl->Text = "Single";
			adt_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Hong Kong";
			lblSUB->Text = System::Convert::ToString(SDhongkong);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (std_btn->Checked && dest_box->Text == "Hong Kong" && chd_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "Standard";
			Ticket_lbl->Text = "Single";
			chd_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Hong Kong";
			lblSUB->Text = System::Convert::ToString(SDhongkong*0.9);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (bsn_btn->Checked && dest_box->Text == "Hong Kong" && adt_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "Business";
			Ticket_lbl->Text = "Single";
			adt_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Hong Kong";
			lblSUB->Text = System::Convert::ToString(Ehongkong);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (bsn_btn->Checked && dest_box->Text == "Hong Kong" && chd_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "Business";
			Ticket_lbl->Text = "Single";
			chd_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Hong Kong";
			lblSUB->Text = System::Convert::ToString(Ehongkong*0.9);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (first_btn->Checked && dest_box->Text == "Hong Kong" && adt_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "First Class";
			Ticket_lbl->Text = "Single";
			adt_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Hong Kong";
			lblSUB->Text = System::Convert::ToString(SThongkong);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (first_btn->Checked && dest_box->Text == "Hong Kong" && chd_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "First Class";
			Ticket_lbl->Text = "Single";
			chd_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Hong Kong";
			lblSUB->Text = System::Convert::ToString(SThongkong*0.9);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (std_btn->Checked && dest_box->Text == "Paris" && adt_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "Standard";
			Ticket_lbl->Text = "Single";
			adt_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Paris";
			lblSUB->Text = System::Convert::ToString(SDfrance);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (std_btn->Checked && dest_box->Text == "Paris" && chd_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "Standard";
			Ticket_lbl->Text = "Single";
			chd_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Paris";
			lblSUB->Text = System::Convert::ToString(SDfrance *0.9);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (bsn_btn->Checked && dest_box->Text == "Paris" && adt_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "Business";
			Ticket_lbl->Text = "Single";
			adt_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Paris";
			lblSUB->Text = System::Convert::ToString(Efrance);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (bsn_btn->Checked && dest_box->Text == "Paris" && chd_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "Business";
			Ticket_lbl->Text = "Single";
			chd_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Paris";
			lblSUB->Text = System::Convert::ToString(Efrance*0.9);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (first_btn->Checked && dest_box->Text == "Paris" && adt_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "First Class";
			Ticket_lbl->Text = "Single";
			adt_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Paris";
			lblSUB->Text = System::Convert::ToString(STfrance);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		if (first_btn->Checked && dest_box->Text == "Paris" && chd_radio->Checked && sing_radio->Checked) {
			class_lbl->Text = "First Class";
			Ticket_lbl->Text = "Single";
			chd_lbl->Text = "YES";
			from_tag->Text = "Delhi";
			To_tag->Text = "Hong Kong";
			lblSUB->Text = System::Convert::ToString(STfrance *0.9);
			lblTAX->Text = System::Convert::ToString(0.20 * System::Convert::ToDouble(lblSUB->Text));
			lblGT->Text = "Rs." + System::Convert::ToString(Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));
			Price_tag->Text = "Rs." + System::Convert::ToString(System::Convert::ToDouble(lblSUB->Text) + System::Convert::ToDouble(lblTAX->Text));

			Random^ random_1 = gcnew Random;
			int Rand_ref = random_1->Next(25000, 55000);
			ref_lbl->Text = System::Convert::ToString(Rand_ref);
		}
		receipt_text->Text = "";
		receipt_text->AppendText("\t\t\t\t" + label15->Text + Environment::NewLine);
		receipt_text->AppendText("****************************************************" + Environment::NewLine);
		receipt_text->AppendText("Booked On" + "\t\t" + __TIMESTAMP__ + Environment::NewLine);
		receipt_text->AppendText(Environment::NewLine);
		receipt_text->AppendText("\t\t\t\t" + "Ref. No." + ref_lbl->Text + Environment::NewLine);
		receipt_text->AppendText("\t\t\t\t" + "Class    " + class_lbl->Text + "\t\t" + Environment::NewLine);
		receipt_text->AppendText("\t\t\t\t" + "Ticket   " + Ticket_lbl->Text + "\t\t" + Environment::NewLine);
		receipt_text->AppendText("***************************************************"+ Environment::NewLine);
		receipt_text->AppendText("\t\t\t\t" + "From   " + from_tag->Text + Environment::NewLine);
		receipt_text->AppendText("\t\t\t\t" + "TO	   " + To_tag->Text + Environment::NewLine);
		receipt_text->AppendText("\t\t\t\t" + "Price   " + Price_tag->Text + Environment::NewLine);
		receipt_text->AppendText("***************************************************");
		receipt_text->AppendText("***************************************************");
		
}
private: System::Void dest_box_SelectedIndexChanged(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void label28_Click(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void To_tag_Click(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void label8_Click_1(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void Price_tag_Click(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void label14_Click(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void button4_Click(System::Object^ sender, System::EventArgs^ e) {
	class_lbl->Text = "";
	Ticket_lbl->Text = "";
	adt_lbl->Text = "";
	from_tag->Text = "";
	To_tag->Text = "";
	Price_tag->Text = "";
	ref_lbl->Text = "";
	lblSUB->Text = "";
	lblGT->Text = "";
	lblTAX->Text = "";
	Route_lbl->Text = "";
}
private: System::Void clear_opt_Click(System::Object^ sender, System::EventArgs^ e) {
	std_btn->Checked = false;
	bsn_btn->Checked = false;
	first_btn->Checked = false;
	dest_box->Text = "Select Destination";
	adt_radio->Checked = false;
	chd_radio->Checked = false;
	sing_radio->Checked = false;
	return_radio->Checked = false;
	receipt_text->Text = "";
}
private: System::Void receipt_text_TextChanged(System::Object^ sender, System::EventArgs^ e) {
	
}
private: System::Void groupBox5_Enter(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void printDocument1_PrintPage(System::Object^ sender, System::Drawing::Printing::PrintPageEventArgs^ e) {
	String^ getstring = receipt_text->Text;
	System::Drawing::Font^ getfont = gcnew System::Drawing::Font("Arial", 16);
	SolidBrush^ getbrush = gcnew SolidBrush(Color::Black);
	PointF getpoint = PointF(150.0F, 150.0F);
	e->Graphics->DrawString(getstring, getfont, getbrush, getpoint);
}
private: System::Void print_Click(System::Object^ sender, System::EventArgs^ e) {
	printPreviewDialog1->Document = printDocument1;
	printPreviewDialog1->ShowDialog();

}
private: System::Void button2_Click(System::Object^ sender, System::EventArgs^ e) {
	if (MessageBox::Show("Do you Want to exit?", "Your App will be terminated", MessageBoxButtons::YesNo, MessageBoxIcon::Question) == System::Windows::Forms::DialogResult::Yes) {
		Application::ExitThread();
	}
	
}
private: System::Void button3_Click(System::Object^ sender, System::EventArgs^ e) {
	about^ box = gcnew about();
	box->ShowDialog();

}
private: System::Void openFileDialog1_FileOk(System::Object^ sender, System::ComponentModel::CancelEventArgs^ e) {
}
private: System::Void MyForm_FormClosing(System::Object^ sender, System::Windows::Forms::FormClosingEventArgs^ e) {
	if (MessageBox::Show("Do you Want to exit?", "Your App will be terminated", MessageBoxButtons::YesNo, MessageBoxIcon::Question) == System::Windows::Forms::DialogResult::Yes) {
		Application::ExitThread();
	}
	else
		e->Cancel = true;
}
};
}
