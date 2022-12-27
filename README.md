# FLO-CLTV-PROJECT
# BG-NBD ve Gamma-Gamma ile CLTV Prediction

# İş Problemi (Business Problem)
FLO satış ve pazarlama faaliyetleri için roadmap belirlemek istemektedir. Şirketin orta uzun vadeli plan yapabilmesi için var olan müşterilerin gelecekte şirkete sağlayacakları potansiyel değerin tahmin edilmesi gerekmektedir.

# Veri Seti Hikayesi
Veri seti son alışverişlerini 2020 - 2021 yıllarında OmniChannel(hem online hem offline alışveriş yapan) olarak yapan müşterilerin geçmiş alışveriş davranışlarından elde edilen bilgilerden oluşmaktadır.

# Degiskenler
            master_id: Eşsiz müşteri numarası
            order_channel : Alışveriş yapılan platforma ait hangi kanalın kullanıldığı (Android, ios, Desktop, Mobile, Offline)
            last_order_channel : En son alışverişin yapıldığı kanal
            first_order_date : Müşterinin yaptığı ilk alışveriş tarihi
            last_order_date : Müşterinin yaptığı son alışveriş tarihi
            last_order_date_online : Muşterinin online platformda yaptığı son alışveriş tarihi
            last_order_date_offline : Muşterinin offline platformda yaptığı son alışveriş tarihi
            order_num_total_ever_online : Müşterinin online platformda yaptığı toplam alışveriş sayısı
            order_num_total_ever_offline : Müşterinin offline'da yaptığı toplam alışveriş sayısı
            customer_value_total_ever_offline : Müşterinin offline alışverişlerinde ödediği toplam ücret
            customer_value_total_ever_online : Müşterinin online alışverişlerinde ödediği toplam ücret
            interested_in_categories_12 : Müşterinin son 12 ayda alışveriş yaptığı kategorilerin listesi


# GÖREVLER

# GÖREV 1: Veriyi Hazırlama
            1. flo_data_20K.csv verisini okuyunuz.Dataframe’in kopyasını oluşturunuz.
            2. Aykırı değerleri baskılamak için gerekli olan outlier_thresholds ve replace_with_thresholds fonksiyonlarını tanımlayınız.
            Not: cltv hesaplanırken frequency değerleri integer olması gerekmektedir.Bu nedenle alt ve üst limitlerini round() ile yuvarlayınız.
            3. "order_num_total_ever_online","order_num_total_ever_offline","customer_value_total_ever_offline","customer_value_total_ever_online" değişkenlerinin
            aykırı değerleri varsa baskılayanız.
            4. Omnichannel müşterilerin hem online'dan hemde offline platformlardan alışveriş yaptığını ifade etmektedir. Herbir müşterinin toplam
            alışveriş sayısı ve harcaması için yeni değişkenler oluşturun.
            5. Değişken tiplerini inceleyiniz. Tarih ifade eden değişkenlerin tipini date'e çeviriniz.

# GÖREV 2: CLTV Veri Yapısının Oluşturulması
            1.Veri setindeki en son alışverişin yapıldığı tarihten 2 gün sonrasını analiz tarihi olarak alınız.
            2.customer_id, recency_cltv_weekly, T_weekly, frequency ve monetary_cltv_avg değerlerinin yer aldığı yeni bir cltv dataframe'i oluşturunuz.
            Monetary değeri satın alma başına ortalama değer olarak, recency ve tenure değerleri ise haftalık cinsten ifade edilecek.


# GÖREV 3: BG/NBD, Gamma-Gamma Modellerinin Kurulması, CLTV'nin hesaplanması
            1. BG/NBD modelini fit ediniz.
                 a. 3 ay içerisinde müşterilerden beklenen satın almaları tahmin ediniz ve exp_sales_3_month olarak cltv dataframe'ine ekleyiniz.
                 b. 6 ay içerisinde müşterilerden beklenen satın almaları tahmin ediniz ve exp_sales_6_month olarak cltv dataframe'ine ekleyiniz.
            2. Gamma-Gamma modelini fit ediniz. Müşterilerin ortalama bırakacakları değeri tahminleyip exp_average_value olarak cltv dataframe'ine ekleyiniz.
            3. 6 aylık CLTV hesaplayınız ve cltv ismiyle dataframe'e ekleyiniz.
                 a. Hesapladığınız cltv değerlerini standarlaştırıp scaled_cltv değişkeni oluşturunuz.
                 b. Cltv değeri en yüksek 20 kişiyi gözlemleyiniz.

# GÖREV 4: CLTV'ye Göre Segmentlerin Oluşturulması
            1. 6 aylık standartlaştırılmış CLTV'ye göre tüm müşterilerinizi 4 gruba (segmente) ayırınız ve grup isimlerini veri setine ekleyiniz. cltv_segment ismi ile dataframe'e ekleyiniz.
            2. 4 grup içerisinden seçeceğiniz 2 grup için yönetime kısa kısa 6 aylık aksiyon önerilerinde bulununuz
