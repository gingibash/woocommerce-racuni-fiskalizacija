# NeZnam računi i fiskalizacija

WooCommerce plugin za izdavanje i fiskalizaciju računa direktno u WordPressu za hrvatsko tržište

## Description

Ovo je plugin za izdavanje fiskaliziranih računa direktno iz WooCommerca na hrvatskom tržištu, bez potrebe za rješenima treće strane.

Plugin prilikom završetka narudžbe, kreira novi račun s odgovarajućim sekvencijalnim brojem računa i izgledom broja računa kako je definirano
u postavkama. Potom ga fiskalizira pozivom na servis Porezne uprave. Sprema JIR/ZKI.

Plugin dodaje informacije o računu u Completed email.

Autor dodatka se odriče bilo kakve odgovornosti za potencijalnu štetu uzrokovanu korištenjem ovog dodatka. Ovaj dodatak je u beta verziji i molim da ga tako i koristite.
Ukoliko imate sumnje da plugin ne radi dobro, prijavite [ovdje](https://github.com/ne-znam/woocommerce-racuni-fiskalizacija/issues)

## Installation

1. Prenesite [zip](https://github.com/ne-znam/woocommerce-racuni-fiskalizacija/releases/download/v0.5.0/neznam-racuni-fiskalizacija.zip) kroz admin sučelje ili FTP
1. Aktivirajte dodatak kroz Dodaci sučelje u WordPressu
1. Namjestite postavke u Postavkama

## Pitanja

### Moram li imati FINA certifikat?

Da, i morate ga namjestiti u postavkama dodatka

### Plugin odbija prihvatiti moj certifikat i lozinku

Ako koristite noviju verziju PHPa (v8) i OpenSSLa (v3) i imate stariji certifikat, onda je moguće da plugin neće prihvatiti vaš certifikat.
Pretvorite certifikate u noviju verziju uz pomoć ovih naredbi:
```
openssl pkcs12 -legacy -in key.p12 -nodes -out key_decrypted.tmp

openssl pkcs12 -in key_decrypted.tmp -export -out key_new.p12
```
ili namjestite ove postavke u /etc/ssl/openssl.cnf

```
[openssl_init]
providers = provider_sect
[provider_sect]
default = default_sect
legacy = legacy_sect
[default_sect]
activate = 1
[legacy_sect]
activate = 1
```

### Mogu li urediti izgled računa?

Možete, samo je potrebno u direktoriju teme dodati datoteku: `woocommerce/neznam/invoice.php` i u njoj urediti izgled računa. Račun se generira uz pomoć [Dompdf](https://github.com/dompdf/dompdf).

### Kome se mogu obratiti za pomoć?

Autor ovog dodatka nudi usluge savjetovanja i namještanja ovog dodatka.

### Mogu li tužiti autora plugina za dobivenu kaznu od Porezne uprave?

Ne, autor se odriče bilo kakve odgovornosti za neispravno korištenje i namještanje ovog dodatka. Vlasnik webshopa i osoba koja ga je namjestila
su same odgovorne za korištenje dodatka koje je rezultiralo kaznom.

## Webshopovi koji koriste ovaj dodatak

- [Maritimo recycling](https://maritimo-recycling.com/)
