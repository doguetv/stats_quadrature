# stats_quadrature

Jeux de données:<br>
data.csv ==> Moyennes sur l'exercice<br>
set1.csv ==> Moyenne sur la série 1 unqiuement

<h2>Etape 1: Test de normalité Shapiro-Wilk</h2>
  Notebook ==>  stats_titouan_normality.ipynb<br>
  Seules les données de l'exercice entier (jeu "data.csv") y sont représentées, mais les deux jeux ont été testés.<br>
  La normalité a été testée sur le pool de données entier puis pour les sous-groupes<br>
    <li>MUSCLE</li>
    <li>GROUPE</li>
    <li>MUSCLE*GROUPE</li>
<br>
Deux nouveaux jeux de données sont créés "data_regression_dataframe.csv" & "set1_regression_dataframe.csv" avec un tri des données.<br>
  /!\ Il a été choisi de conserver les données expérimentales et pas les données transformées suite aux tests de normalité pouyr les sous-groupes.<br>

<h2>Etape 2: Régressions </h2>
  Notebooks ==> stats_titouan_regression_whole.ipynb (exercice entier, basé sur le jeu de données "data_regression_dataframe.csv")<br>
            ==> stats_titouan_regression_set1.ipynb (série 1 uniquement, basé sur le jeu de données "set1_regression_dataframe.csv")<br>
  <h3>Regressions simples</h3>
    Pour les deux jeux de données des regressions simples ont été réalisées pour le pool entier et pour les sous-groupes selon :<br>
      <li>1/ SWE_raw (variations absolues PRE-POST) comme variable dépendante et ['Activation', 'Lrelative, 'F_V', 'ForceRelative'] comme variables indépendantes.</li>
      2/ Entre les variables indépendantes elles-mêmes pour mettre en relief la colinéarité multiple.</li>
  <h3>Regressions pas à pas + multiple</h3>
    Pour les deux jeux de données la procédure suivante a été utilisée et ce pour tous les sous-groupes (MUSCLE & GROUPE):
      <li>1/ Stepswise regression ==> objectif, identifier les 3 variables indépendantes expliquant le mieux la variation de la variable dépendante (SWE_raw)</li>
      <li>2/ Les 3 meilleurs variables indépendantes sont conservées pour une regression multiple avec SWE (Dépendante) et (x3 Indep).</li>
      <li>3/ L'équation de la régression multiple est stockée dans deux nouveaux jeux de données ("data_[...]_coefficients.csv" & "set1_[...]_coefficients.csv").</li>
<h2>Etape 3: Validation</h2>
