# Remotejobb: Sök jobb i Sverige

Sök bland lediga jobb i Sverige direkt i Claude. Fråga som du pratar, på svenska eller engelska, och få aktuella annonser med länk till ansökan.

## Vad pluginet gör

- **Söker jobb** på nyckelord, stad, kategori, företag, anställningsform, lägsta månadslön och hur nyligen jobbet publicerades. Du kan också filtrera på distans eller hybrid och på var du får bo.
- **Visar ett jobb i sin helhet** (när källan tillåter det), med lön, anställningsvillkor, sista ansökningsdag och ansökningslänk.
- **Listar kategorier och städer** som har lediga jobb just nu.

Pluginet innehåller kopplingen till Remotejobbs MCP-server och en skill, `sok-jobb`, som hjälper Claude att välja rätt filter, visa resultaten tydligt och bredda sökningen när inget matchar.

## Testa att fråga

- "Hitta deltidsjobb inom kundtjänst som jag kan göra hemifrån"
- "Visa jobb i Stockholm som publicerats den senaste veckan"
- "Sammanfatta kraven för det första jobbet och ge mig ansökningslänken"

## Vad som skickas och vart

Pluginet ansluter till en enda server: `https://remotejobb.se/mcp`. Claude skickar bara det som behövs för sökningen, till exempel sökord, filter och jobb-id. Ingen inloggning eller nyckel behövs, och pluginet kör inga skript eller program på din dator.

Kopplingen kan bara läsa. Den kan inte söka jobb åt dig, skicka meddelanden eller ändra något. Du söker alltid jobbet direkt hos arbetsgivaren eller källan.

Jobben kommer från Platsbanken (Arbetsförmedlingens öppna data), arbetsgivares egna karriärsidor och andra jobbsajter.

## Integritet och support

- Integritetspolicy: https://remotejobb.se/integritetspolicy
- Om kopplingen: https://remotejobb.se/ai
- Support: support@remotejobb.se

Utgivare: J. Melker Bengtsson AB
