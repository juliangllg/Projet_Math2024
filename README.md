# SAEMATH

##Exercice 1

###1)

```
// Charger les données du fichier data.csv
data_nbr = csvRead('data.csv');
data_txt = csvRead('data.csv', [], [], 'string');

// Initialisation des variables
genres = data_txt(:, 3);
nb_homme = sum(genres == 'Male');
nb_femme = sum(genres == 'Female');
nb_other = sum(genres == 'Other');

//Affichage du graphe
pie([nb_homme, nb_femme,nb_other], ['Homme', 'Femme','Other']);
title('Répartition des genres');
legend('Homme', 'Femme', 'Other');
```

![alt text](./Images/Ex1_1.png)

###2

```
// Charger les données du fichier data.csv
data_nbr = csvRead('data.csv');
data_txt = csvRead('data.csv', [], [], 'string');

// Initialisation des variables issues des données du fichier data.csv
genders = data_txt(:, 3);
education_levels = data_nbr(:, 4);

// Nombre de diplomé pour chaque combinaison de genre et de niveau d'études
male_HS = sum(genders == 'Male' & education_levels == 0);
male_bachelor = sum(genders == 'Male' & education_levels == 1);
male_master = sum(genders == 'Male' & education_levels == 2);
male_Phd = sum(genders == 'Male' & education_levels == 3);

female_HS = sum(genders == 'Female' & education_levels == 0);
female_bachelor = sum(genders == 'Female' & education_levels == 1);
female_master = sum(genders == 'Female' & education_levels == 2);
female_Phd = sum(genders == 'Female' & education_levels == 3);


other_HS = sum(genders == 'Other' & education_levels == 0);
other_bachelor = sum(genders == 'Other' & education_levels == 1);
other_master = sum(genders == 'Other' & education_levels == 2);
other_Phd = sum(genders == 'Other' & education_levels == 3);

// Données pour le graphe

// Pour les hommes
male_data = [male_HS, male_bachelor, male_master, male_Phd];


// Pour les femmes
female_data = [female_HS, female_bachelor, female_master, female_Phd];


// Pour les autres genres
other_data = [other_HS, other_bachelor, other_master, other_Phd];

// Affichage du graphe
bar([male_data' female_data' other_data']);
title("Répartition diplôme par genre");
xlabel("Niveau education");
ylabel("Nombre de diplômés");
xtick_labels = ["HS", "Bachelor", "Master", "PhD"];
xtitle(xtick_labels);
legend(["Hommes", "Femmes", "Autres"]);

```
![image Ex1.2] (./Images/Ex1_2.png)

###3
```
// Charger les données du fichier data.csv
data_txt = csvRead('data.csv', [], [], 'string');

// Initialisation des variables a partir du fichier data.csv
professions = data_txt(:, 5);

// Trouver les professions uniques et compter les occurrences
[unique_professions, idx] = unique(professions, "r");
counts = zeros(size(unique_professions, 1), 1);

for i = 1:size(unique_professions, 1)
    counts(i) = sum(strcmp(professions, unique_professions(i)));
end

// Trier les professions par ordre décroissant d'effectifs
[sorted_counts, sort_idx] = gsort(counts, "g");
sorted_professions = unique_professions(sort_idx);


// Sélectionner les 10 professions les plus représentées
top_10_counts = sorted_counts(1:10);
top_10_professions = sorted_professions(1:10);

//Affichage du graphe
bar(top_10_counts);
title("Effectifs des 10 professions les plus représentées");
xlabel("Professions");
ylabel("Nombre de personnes");
set(gca(), "xticklabels", top_10_professions);
xtitle(top_10_professions);
set(gca(), "x_tick_angle", 45);
```

![image ex1.3](./Images/Ex1_3.png)


