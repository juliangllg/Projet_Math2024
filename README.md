# SAEMATH

data_nbr = csvRead('data.csv');
data_txt = csvRead('data.csv', [], [], 'string');


genres = data_txt(:, 3);


nb_homme = sum(genres == 'Male');
nb_femme = sum(genres == 'Female');
nb_other = sum(genres == 'Other');
pie([nb_homme, nb_femme,nb_other], ['Homme', 'Femme','Other']);
title('Répartition des genres');
legend('Homme', 'Femme', 'Other');


