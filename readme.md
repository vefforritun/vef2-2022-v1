# Vefforritun 2, 2022. Verkefni 1: Gagnavinnsla

[Kynning á verkefni í tíma](https://youtu.be/ow9NdluaWCs?t=110).

Þér er falið það verkefni að útbúa gagnavinnslutól sem tekur við tölulegum gögnum, keyrir tölfræðilega vinnslu á þau og útbýr vef sem skilar niðurstöðum.

## Markmið

Eftirfarandi eru markmið verkefnisins:

* Rifja upp (og í einhverjum tilfellum kynnast) vefforritun 1: HTML, CSS, og þau tæki og tól sem við notuðum þar.
* Nota Node.js til að eiga við og lesa gögn úr skráarkerfinu.
* Setja upp og nota test framework til að útbúa test meðfram því sem við skrifum forritið (eða eftir, viljum a.m.k. skrifa test!)
* Setja upp verkefni og CI pípu sem gefur út á Netlify eftir að verkefni með test sem keyra er pushað á `main` branch í git.

Hverjum hluta er lýst nánar að neðan.

Athugið að það er mjög mögulegt að einhver hluti af verkefninu taki hlutfallslega lengri tíma en hinir, og þá sérstaklega með tilliti til hversu mikið hlutinn vegur í mati. Vegið og metið því hvar þið eyðið tíma og ef þið festist, hafið samband við kennara, dæmatímakennara eða spyrjið á `#vef2-2022` á Slack.

### HTML, CSS og útlit

Setja skal upp merkingarfræðilegt HTML með útliti sem notar flexbox eða grid. Ekki er krafa um flókið útlit og ekki er gefin fyrirmynd.

Forsíða skal hafa titil (t.d `Gagnavinnsla`) og lista af öllum gagnasettum sem hafa tengla yfir á hverja keyrslu. Að minnsta kosti skal birta nafn gagnasetts en leyfilegt er að birta eitthvað af niðurstöðum.

Á síðu fyrir gagnasett skal birta á skýran máta tölulegagreiningu ásamt öllu gagnasettinu, einnig skal vera tengill til baka á forsíðu.

Leyfilegt er að nota template mál, en einnig er í lagi að nota strengjavinnslu/template strengi í JavaScript til að útbúa HTML, sjá dæmi í tíma.

Hægt er að skoða sýnilausn á [verkefni 4](https://github.com/vefforritun/vef1-2021-v4-synilausn) eða [verkefni 5](https://github.com/vefforritun/vef1-2021-v5-synilausn) í vef1-2021.

### Tæki og tól, skipulag og „snyrtilegur“ kóði

Setja skal upp að minnsta kosti `eslint` og `stylelint` fyrir JavaScript og CSS. Einnig er leyfilegt að setja upp `prettier`.

Fyrir `stylelint` skal fylgja því sem uppsett var í [verkefni 6](https://github.com/vefforritun/vef1-2021-v6-synilausn) í vef1-2021.

Fyrir `eslint` og `prettier` skal fylgja því sem uppsett var í [verkefni 9](https://github.com/vefforritun/vef1-2021-v9-synilausn) í vef1-2021.

### Lestur á gögnum

Í möppunni `./data` eru gefnar 12 skrár með gögnum. Þessi gögn má hugsa sem útkomu úr _einhverri keyrslu_, okkur er sama hverri. Verkefni okkar er að keyra „tölulegagreiningu“ á gögnin (hér er niðurstaða og réttleiki ekki aðalatriði heldur að hafa eitthvað til að reikna) og finna:

* Frávik (variance)
* Hæsta gildi (max)
* Meðaltal (mean)
* Miðgildi (median)
* Minnsta gildi (min)
* Staðalfrávik (standard deviation)
* Summu (sum)
* Svið (range)

Að útreikningar séu 100% réttir er fínt, en ekki eitt af markmiðum verkefnisins.

Leyfilegt er að sækja forritasafn af NPM sem sér um þessa útreikninga.

Um gögnin gildir:

* Almennt uppsett sem ein tala per línu í skjali.
* Hver tala er á formi sem JavaScript styður: heiltölur, rauntölur, veldisritháttur (scientific notation) og stórar tölur (`BigInt`)
  * Bæði jákvæðar og neikvæðar
  * _Nema_ rauntölur eru á íslensku formi: `123,456` ekki `123.456`
  * _Nema_ tölur geta verið með þúsundaskiltákn (thousand separator): `1.000.000,123` er talan `1000000.123` fyrir JavaScript
* Athugasemdir í skjali eru á forminu `# Athugasemd` per línu
* Gögn geta verið spillt
  * Það geta verið tómar línur/bil í línum sem skal hunsa
  * Það geta verið textabrot sem ekki eru innan athugasemda
  * Það geta verið ógildar tölur, þær skal *ekki* lesa/taka með í útreikning, t.d. `100aa` og `aa100` eru ólöglegar tölur

Fyrir hvert gagnasett skal því:

* Lesa upp tölur miðað við forsendur að ofan
* Fyrir allar gildar tölur framkvæma útreikninga
* Skila niðurstöðu á sér vefsíðu sem birtir útreikninga ásamt öllu gagnasetti, hvort sem er upprunalega eða þáttuðu (parsed)

Ef gagnasett hefur engar niðurstöður/aðeins óleyfileg gögn skal taka það fram en ekki sleppa.

Einnig skal vera forsíða sem tengir yfir á hvert gagnasett, heiti skal vera heiti skráar.

### Test

Setja skal upp lausn þannig að hægt sé að skrifa próf. Það þýðir að skipta skal upp forriti í einingar sem:

* les skrár úr möppu
* þáttar (parse) gögn úr skrá
* framkvæmir útreikninga á þáttuðu setti
* setur saman HTML til birtingar

Að minnsta kosti tvær af fjórum einingum skulu hafa 100% line coverage, allar einingar skulu hafa próf.

Leyfilegt er að skipta enn frekar upp.

Þó að notað sé forritasafn af NPM skal skrifa próf fyrir það og hvernig það er notað.

### Netlify

Setja skal upp vefinn með niðurstöðum á Netlify tengt við GitHub, sjá dæmi í tímum.

## Mat

Fullt hús stiga fæst ef allt sem nefnt er innan hvers markmiðs er að fullu útfært og virkar.

* 25% Lestur á gögnum
* 25% Test
* 20% HTML, CSS og útlit
* 15% Tæki og tól
* 15% Netlify

## Sett fyrir

Verkefni sett fyrir í fyrirlestri miðvikudaginn 19. janúar 2022.

## Skil

Skila skal í Canvas í seinasta lagi fyrir lok dags föstudaginn 4. febrúar 2022.

Skil skulu innihalda:

* Slóð á verkefni keyrandi á Netlify
* Slóð á GitHub repo fyrir verkefni. Dæmatímakennurum skal hafa verið boðið í repo. Notendanöfn þeirra eru:
  * `MarzukIngi`
  * `WhackingCheese`

---

> Útgáfa 0.1

| Útgáfa | Breyting      |
|--------|---------------|
| 0.1    | Fyrsta útgáfa |
