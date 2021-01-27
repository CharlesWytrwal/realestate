# RealEstate modeling

Projekt, którego zamysłem jest stworzenie modelu, który na podstawie zmiennych będzie przewidywał ceny nieruchomości w Warszawie.

1. RealEstate_cleaning_database.ipynb - notebook pomocniczy. W tym notebooku przeprowadzono transformacje zbioru danych. 
- wprowadzono funkcje pomocnicze przy pomocy których zostały wyciągnięte wartości z kolumn. Część z nich są słownikami (klucz:wartość) a część listami. Wartości zostają wyciągnięte do odpowiedniej kolumny dodatkowo stosując odpowiedni filtr w zależności od typu zmiennej
- do zmiennej all_benefits została przypisana funkcja set(), której zadaniem jest wyodrębnienie unikalnych wartości z kolumny extra_benefits
- w kolumnie kosztu została przeprowadzona transformacja miejsc dziesiętnych (z przecinka na kropkę) tak aby można było ją zrzutować do float
- naprawa wartości w poszczególnych cechach (bug podczas gromadzenia danych), wyciągnięcie ich do osobnych kolumn
- zastosowanie tego samego zabiegu dla extra_description co dla extra_benefits

2. Model.ipynb - w tym notebooku operacje przeprowadzane są na oczyczonym zbiorze danych.
- wybór zmiennej docelowej - price, w kolumnie znajduje się 268 wierszy z wartościami NaN oraz 1748 wierszy gdzie wartość wynosi -1. Autor na tym etapie budowania modelu decyduje się usunąć problematyczne wiersze ze zmiennej train
- autor będzie operował na 17128 obiektach, które zawierają cechę price
- przeprowadzenie transformacji logarytmicznej oraz obcięcie po 1% z tzw. "ogona" by rozkład stał się bardziej symetryczny (czyt. przypominał normalny)
- próba stworzenia pierwszego głupiego modelu tzw. dummy model. Jako metrykę sukcesu Autor wybrał RMSLE ze względu na outliers czyli wartości odstające.
- uzyskany wynik 1.068 będzie benchmarkiem dla przyszłych eksperymentów
- Autor robi porządek w kodzie tak aby łatwiej przeprowadzać późniejsze eksperymenty
- gdy jako DummyRegressor została zastosowana strategia mediany dała lepszy rezultat (0.665) jendak po analizie krzywej uczenia można wywnioskować, że model "zgadł" medianę i zawsze zwraca taką samą wartość. 

Co należałoby zrobić dalej?
-
- sprawdzić inne modele np. RandomForest 
- zwiększyć złożoność modelu
- feature enineering 
- wybrać najlepiej działający model
- przeprowadzić selekcję cech np. na podstawie ich ważności
- przeprowadzić optymalizację modelu tak aby uzyskać jak najlepszy wynik

 
