# ![q](https://i.hizliresim.com/7cyf88f.png)kokturkdash-cyber
![header](https://i.hizliresim.com/cxxmzzo.png)

![GitHub package.json version](https://img.shields.io/github/package-json/v/atailh4n/kokturkdash-cyber?color=356F50&label=VERS%C4%B0YON&style=for-the-badge) ![npm bundle size (version)](https://img.shields.io/bundlephobia/min/kokturkdash-cyber/0.0.1-beta?color=356F50&label=BOYUT&style=for-the-badge) ![npm](https://img.shields.io/npm/dm/kokturkdash-cyber?color=356F50&label=AYLIK&style=for-the-badge)

**[kokturkdash](https://npmjs.com/packages/kokturkdash) için tema modülüdür.**

# 😎0.0.2-public Sürümü Güncellemesi:
* Tema düzeltmeleri
* kokturkdash 0.0.4-public için uyumluluk
* Yeni class ve callback uyumluluğu

# 🤔Nasıl İndirilir
```js
npm i kokturkdash
```

# 😍Görünüm
![image1](https://i.hizliresim.com/9lvlvjh.png)
![image2](https://i.hizliresim.com/6h67i7f.png)
![image3](https://i.hizliresim.com/pmg0pta.png)
![image4](https://i.hizliresim.com/3ttxm6t.png)

# 📑Tam Örnek
[kokturkdash](https://npmjs.com/packages/kokturkdash) modülü ile kullanılır:
```js
const kokturkdash = require('kokturkdash')
const Discord = require('discord.js');
const Cyber = require('kokturkdash-cyber');
const client = new Discord.Client();
client.login('token');

let dil = {};

let hosgeldinmesaji = {};

let booster = {};

let logsys = {};

let sysactive = {};

const WebPanel = new kokturkdash.PanelIcerik({

    port: 80, // Glitch için 3000 önerilir.
    client: {
        id: 'clientID',
        secret: 'clientSecret'
    },
    yonlendirmeUrl: 'http://localhost/discord/callback',
    domain: 'http://localhost',
    bot: client,
    websiteBaslik: "Köktürk Dash",
    iconURL: 'http://cdn.kokturkbot.ga/logos/kokturklogo.jpg',
    tema: Cyber({
        websiteIsim: "Kokturk Dash Cyber",
        iconURL: "https://cdn.discordapp.com/emojis/866989137868750858.png?v=1",
        girismenu: {
            headerkart:{
                title: "Köktürk - 1# Numaralı Discord Botu",
                description: "Köktürk bot'un web paneline hoşgeldiniz! Burdan sunucunuzu yönetebilir ve düzenleyebilirsiniz! <strong>Geliştiricim ile iletişim için: Instagram: @atailh4n</strong>",
                image: "https://i.hizliresim.com/mbg20ij.jpg",
            },
            bilgiler: {
                title: "Bilgiler",
                description: "Sunucuları yönetmek için <a href='/manage'>Sunucu Yönetim Sayfasına</a> gidin.<br><br>Tüm komutları görmek için <a href='/commands'>Komutlar sayfasına</a> bakın.</br></br>"
            },
            basliklar: {
                title: "Durum",
                list: [
                    {
                        icon: "fa fa-user",
                        text: "Kullanıcı arayüz sürümü",
                        timeText: "Cyber v0.0.1-beta",
                        bg: "bg-light-info"
                    },
                    {
                        icon: "fa fa-server",
                        text: "Downtime",
                        timeText: "Downtime yaşanmadı.",
                        bg: "bg-light-danger"
                    }
                ]
            }
        },
        komutlar: {
            sayfaBasligi: "Komutlar",
            table: {
                title: "Liste",
                subTitle: "Tüm Komutlar",
                ikidil: true,
                list:
                [
                    {
                        komutIsmi: "Ban",
                        komutKullanim: "prefix.kick <arg> [op]",
                        komutKullanimEN: "prefix.kick <arg> [op]",
                        komutAciklama: "Lorem ipsum dolor sth",
                        komutAciklamaEN: "Lorem ipsum dolor sth"
                    },
                    {
                        komutIsmi: "Kick",
                        komutKullanim: "prefix.kick <arg> [op]",
                        komutKullanimEN: "prefix.kick <arg> [op]",
                        komutAciklama: "Lorem ipsum dolor sth",
                        komutAciklamaEN: "Lorem ipsum dolor sth"
                    }
                ]
            }
        }
    }),
    ayarlar: [
        {
            kategoriID: 'setup',//Kategori ID benzersiz(unique) olmalıdır!
            kategoriIsim: "Kurulum",// Kategori İsmi
            kategoriSecimListesi: [//Kategorinin içindeki elementler buraya yazılcak!
                {//Element Başlangıç
                    secimID: 'lang', //ID kısmı benzersiz(unique) olmalıdır!
                    secimIsim: "Dil", //Başlık Kısmı
                    secimAciklama: "Botun dilini seçin.", //Açıklama kısmı
                    secimTipi: kokturkdash.formTipleri.secenekler({"Türkçe": "tr", "İngilizce": "en"}, false),//Seçim obje tipi
                    //Var olan veriyi kontrol ediyoruz ve yazdırıyoruz
                    normalVeri: async ({guild}) => {//async kullanmaya özen gösterin! Veritabanları için gereklidir. (Normal veri başlangıcı)
                        return dil[guild.id] || null;//Veriyi veritabanından çekince ya veri görüntülenecek yada boş dönecek
                    },//Normal veri bitişi
                    //Yeni veriyi ayarlıyoruz
                    yeniVeri: async ({guild,newData}) => {//Yeni veri başlangıcı
                        dil[guild.id] = newData;//Veriyi veritabanına kaydet
                        //Quick.db için örnek: await db.set(`dil.${guild.id}`, newData)
                        //Mongoose için örnek: await ModelName.findOneAndUpdate({ key: guild.id }, {$set: { key2: newData}}, {new: true});
                        return;
                    }//Yeni veri bitişi
                },//Element Bitiş
                {
                    secimID: 'log_ch',
                    secimIsim: "Log Kanalı",
                    secimAciklama: "Logların nereye atılacağını seçin.",
                    secimTipi: kokturkdash.formTipleri.kanalSecici(false),
                    normalVeri: async ({guild}) => {
                        return logsys[guild.id] || null;
                    },
                    yeniVeri: async ({guild,newData}) => {
                        console.log();[guild.id] = newData;
                        return;
                    }
                },
                {
                    secimID: 'sys_aktif',
                    secimIsim: "Loglama Aç/Kapat",
                    secimAciklama: "Loglama açıp kapamaya yarar.",
                    secimTipi: kokturkdash.formTipleri.tik(false, false),
                    normalVeri: async ({guild}) => {
                        return sysactive[guild.id] || null;
                    },
                    yeniVeri: async ({guild,newData}) => {
                        sysactive[guild.id] = newData;
                        return;
                    }
                },
            ]
        },
        {
            kategoriID: 'other',
            kategoriIsim: "Diğer",
            kategoriSecimListesi: [
                {
                    secimID: 'booster_rol',
                    secimIsim: "Booster Rolü",
                    secimAciklama: "Booster Rolünü seçin.",
                    secimTipi: kokturkdash.formTipleri.rolSecici(false),
                    normalVeri: async ({guild}) => {
                        return booster[guild.id] || null;
                    },
                    yeniVeri: async ({guild,newData}) => {
                        booster[guild.id] = newData;
                        return;
                    }
                },
                {
                    secimID: 'hosgeldin_msj',
                    secimIsim: "Hoşgeldin Mesajı",
                    secimAciklama: "Hoşgeldin mesajı girin.",
                    secimTipi: kokturkdash.formTipleri.metingirisi("Lütfen metin girin...", 7, 30, false, false),
                    normalVeri: async ({guild}) => {
                        return hosgeldinmesaji[guild.id] || null;
                    },
                    yeniVeri: async ({guild,newData}) => {
                        hosgeldinmesaji[guild.id] = newData;
                        return;
                    }
                },
            ]
        },
    ]
})

WebPanel.calistir();
```

# İletişim
[Instagram](https://instagram.com/atailh4n): @atailh4n

Discord:Ata İlhan#2077
