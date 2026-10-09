# Audyt-odporno-ci-hase-z-John-the-Ripper
Cel zadania
Po ukończeniu ćwiczenia potrafisz:

przeprowadzić atak słownikowy offline na przygotowanym hashu testowego hasła;
porównać użycie surowego SHA-256 i bcrypt do przechowywania haseł;
wyjaśnić wpływ soli oraz kosztu obliczeniowego;
odróżnić znalezienie hasła metodą zgadywania od „odszyfrowania hasha”.
Pracuj wyłącznie na danych przygotowanych na potrzeby tego ćwiczenia. Nie używaj swoich prawdziwych haseł ani hashy z kont i systemów produkcyjnych.

Organizacja pracy
Jedna osoba w parze tworzy hashe (autor), a druga próbuje odzyskać hasło za pomocą Johna (audytor). Autor przekazuje audytorowi tylko przygotowany hash, bez podawania wybranego hasła. Po pierwszej części możecie zamienić się rolami.

Autor wybiera jedno testowe hasło z poniższej puli:

Kurs2026!
LearnIT2026!
Haslo123!
Audytor przygotowuje własny mały słownik. Powinien zawierać wszystkie trzy hasła z puli oraz kilka innych kandydatów. Dzięki temu wynik ćwiczenia nie zależy od pobierania dużego słownika z internetu.

Etap 1. Szybki hash SHA-256
Autor tworzy surowy hash SHA-256 wybranego hasła i zapisuje go w pliku w formacie zrozumiałym dla Johna. Sprawdza, czy przy hashowaniu nie dodał przypadkowo znaku nowej linii.
Audytor otrzymuje wyłącznie plik z hashem i uruchamia przeciwko niemu atak słownikowy w John the Ripper.
Audytor zapisuje znalezione hasło oraz obserwuje, jakiego typu hash przetwarzał program.
Autor potwierdza, czy znalezione hasło zgadza się z oryginałem.
Do zanotowania: Czy sam hash pozwolił odczytać hasło, czy program musiał testować kolejne kandydatury?

Etap 2. To samo hasło zapisane z bcrypt
Autor generuje hash bcrypt tego samego hasła, ustawiając koszt obliczeniowy na 10. Przekazuje audytorowi plik z hashem.
Audytor używa tego samego słownika co w etapie 1 i wybiera w Johnie odpowiedni typ hasha.
Zapiszcie, czy hasło udało się znaleźć oraz co zauważyliście w działaniu programu.
Mały słownik może zakończyć oba testy bardzo szybko. Jeżeli nie widać różnicy gołym okiem, skorzystajcie z funkcji testu wydajności Johna i porównajcie tempo sprawdzania kandydatów dla obu formatów. Nie traktujcie wyniku jako stałej wartości dla wszystkich komputerów.

Do zanotowania: Czy użycie bcrypt sprawiło, że hasło obecne w słowniku stało się nieodgadywalne? Co zmienił koszt obliczeniowy?

Etap 3. Wpływ soli
Autor tworzy dwa osobne hashe bcrypt tego samego hasła i przypisuje je dwóm różnym testowym użytkownikom. W obu przypadkach używa tego samego kosztu.
Porównajcie same wartości hashy, pomijając nazwy użytkowników.
Zastanówcie się, co atakujący zobaczyłby w bazie, gdyby wielu użytkowników miało to samo hasło, ale każdy hash miał własną sól.
Do zanotowania: Czy hashe są identyczne? Czy różne wartości dowodzą, że użytkownicy mają różne hasła?

Etap 4. Granica ataku słownikowego
Usuńcie ze swojego słownika hasło wybrane przez autora i powtórzcie próbę na testowym hashu. Nie korzystajcie na razie z innego słownika ani dodatkowych reguł generowania kandydatów.

Do zanotowania: Co oznacza brak znalezionego hasła? Czy jest to dowód, że hasła nie da się odgadnąć żadną inną metodą?

Wyniki do oddania
Przygotujcie krótką notatkę, maksymalnie jedną stronę, zawierającą:

Test	Czy znaleziono hasło?	Co zaobserwowaliście?	Jaki jest wniosek?
SHA-256, hasło w słowniku			
bcrypt, hasło w słowniku			
Dwa hashe bcrypt tego samego hasła			
Hasło usunięte ze słownika			
Odpowiedzcie również własnymi słowami na trzy pytania:

Dlaczego ograniczenie liczby prób logowania nie zatrzyma atakującego, który zdobył kopię bazy hashy?
Jakie oddzielne problemy rozwiązują sól i koszt obliczeniowy?
Jaki mechanizm przechowywania haseł wybralibyście do nowej aplikacji i dlaczego?
