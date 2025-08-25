# h1 - Oma Linux

## Tiivistykset luetuista lähteistä

- Vapaan ohjelmiston (Open Source) 4 keskeistä ominaisuutta ovat:
    * Vapaus käyttää ohjelmistoa mihin tahansa tarkoitukseen
    * Vapaus tutkia ohjelmistoa ja muuttaa sitä. Tämä edellyttää vapaata pääsyä ohjelmiston lähdekoodiin.
    * Vapaus jakaa kopioita ohjelmistosta.
    * Vapaus jakaa kopioita muokatusta ohjelmistosta.
- Ohjelmistoon liittyvien ohjeiden / manuaalien tulee olla myös vapaasti saatavilla
Lähteet: https://www.gnu.org/philosophy/free-sw.html, Välimäki 2005 (http://lib.tkk.fi/Diss/2005/isbn9529187793/isbn9529187793.pdf).

- Vapaan ohjelmiston (Open Source) määritelmässä ei edellytetä moraalisia oikeuksia, patentteja, rajoitettuja omistusoikeuksia, minimivaatimuksia, yhteentoimivuuden vaatimuksia tai sitä, että lisenssien tulisi olla oikeudellisesti sitovia (Välimäki 2005).
-	On hyvä muistaa, että Open Source -määritelmät ovat aina tulkinnanvaraisia, ja niiden soveltaminen vaatii aina tapauskohtaista harkintaa (https://www.gnu.org/philosophy/free-sw.html).

## Raportti virtuaalikoneen ja Linuxin asennuksesta

Asennus aloitettu ma 25.8. klo 16:00. Laitteena Asus Vivobook S14. 

Asennuksessa hyödynnetty kurssiohjeita https://github.com/johannaheinonen/johanna-test-repo/blob/main/linux-20082025.md ja https://terokarvinen.com/2021/install-debian-on-virtualbox/.

Ladattu Virtualbox-asennustiedosto https://www.virtualbox.org/wiki/Downloads.

Asennustiedoston käynnistäessä tullut virhesanoma:

<img width="311" height="200" alt="Virhe_1" src="https://github.com/user-attachments/assets/b19f8a6d-a082-4512-9137-d545f0e12c98" />

Etsitty apua virtualboxin keskustelufoorumilta https://forums.virtualbox.org/viewtopic.php?t=108556 ja Microsoftin ohjesivuilta rhttps://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#latest-microsoft-visual-c-redistributable-version, joista löydetty ratkaisu. 

Ladattu tarvittavat päivitykset https://aka.ms/vs/17/release/vc_redist.x64.exe. Päivityksen jälkeen asennustiedoston käynnistäminen onnistui. Aikaa virheen paikantamiseen ja korjaamiseen meni alle 5 minuuttia.

Ladattu Debian ISO image https://cdimage.debian.org/debian-cd/13.0.0-live/amd64/iso-hybrid/. Latauksessa kesti noin 10 minuuttia.

Testattu verkkoselaimen toimivuus (klikattu application -> web browser) ja näppäimistö terminal-ikkunassa, bootattu virtuaalikone (klikattu debian live user -> shutdown ja aloitettu varsinainen asennus aiemmin mainittujen kurssiohjeiden mukaisesti. 

Valittu kieleksi englanti, sijanniksi Suomi, kielipaketiksi en_US.UTF-8, näppäimistöksi Suomi.

Valittu host-name: linux-test, domain-name: example.com, asetettu käyttäjänimi ja salasana. Suoritettu asennus ohjeen https://github.com/johannaheinonen/johanna-test-repo/blob/main/linux-20082025.md mukaisesti loppuun.

Päivitetty ohjeen https://github.com/johannaheinonen/johanna-test-repo/blob/main/linux-20082025.md kohdan 5. mukaisesti sources.list, sillä update ei toiminut ilman sitä. 

Päivitetty ohjeen https://terokarvinen.com/2021/install-debian-on-virtualbox/ mukaiseti komennolla $ sudo apt-get -y dist-upgrade kaikki päivitettävä.

Asennettu ja käynnistetty palomuuri ohjeen https://terokarvinen.com/2021/install-debian-on-virtualbox/ mukaisesti komennoilla:
$ sudo apt-get -y install ufw
$ sudo ufw enable

Koko asennussaagass mennyt noin 1 tunti ja 50 minuuttia, joista iso osa mennyt kuitenkin allekirjoittaneen ihmettelyyn ja kokeiluun asennuksen jälkeen, sillä olen täysin noviisi aiheen ympärillä. Varsinaiset asennuksessa vastaan tulleet haasteet sain nopeasti ratkottua kurssiohjeiden ja pikaisen googlailun avulla.
