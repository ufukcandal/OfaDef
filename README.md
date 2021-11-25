# OfaDef
--------------------------------------------------------------------------------OfaDef Source Code-------------------------------------------------------------------------------

  string msg = ("<script type = 'text/javascript'>alert('Girliğiniz Parola Kurallara Uygun Değildir Lütfen Tekrar Deneyin');" + "<" + "/script>");

        if (Parola.Text.Length < 11)
        {
            Response.Write(msg);
        }
        else
        {
            string paroladoğrulamatxt = Parola.Text;
            char[] rakamlar = paroladoğrulamatxt.ToCharArray();
            int kural1 = 0;
            for (int i = 0; i < 10; i++)
            {
                kural1 += Convert.ToInt32(rakamlar[i].ToString());
            }
            char[] birlerbasamagikural1 = kural1.ToString().ToCharArray();
            if (rakamlar[0].ToString() == "0")
            {
                string sıfırmesaj = ("<script type = 'text/javascript'>alert('İlk Basamak 0 Olamaz Lütfen Farklı Bir Rakam Giriniz !..');" + "<" + "/script>");
                Response.Write(sıfırmesaj);
            }
            else
            {

                char[] birlerbas1 = kural1.ToString().ToCharArray();
                int tekler = 0;
                int ciftler = 0;
                for (int i = 0; i < 10; i += 2)
                {
                    tekler += Convert.ToInt32(rakamlar[i].ToString());
                }
                for (int i = 1; i < 9; i += 2)
                {
                    ciftler += Convert.ToInt32(rakamlar[i].ToString());
                }
                int toplam = (tekler * 7) + (ciftler * 9);
                char[] onuncubasamak = toplam.ToString().ToCharArray();

                int onbirincibasamak = 0;
                for (int i = 0; i < 10; i++)
                {
                    onbirincibasamak += Convert.ToInt32(rakamlar[i].ToString());
                }
                char[] onbirincibasamakharf = onbirincibasamak.ToString().ToCharArray();
                if ((rakamlar[9] == onuncubasamak[onuncubasamak.Length - 1]) && (rakamlar[10] == onbirincibasamakharf[onbirincibasamakharf.Length - 1]))
                {
                    Parola.Visible = false;
                    Kontrol.Visible = false;
                    komut.Visible = true;
                    calistir.Visible = true;
                    KomutTxT.Visible = true;
                    yazi1.Visible = false;
                    yazi2.Visible = false;
                }
                else
                {
                    string sıfırmesaj = ("<script type = 'text/javascript'>alert('Kurallara Uygun Değildir Lütfen Tekrar Deneyin !..');" + "<" + "/script>");
                    Response.Write(sıfırmesaj);

                }

            }
        }
