5.) Ecrivons ce script interactif :

SET MARKUP HTML ON SPOOL ON PREFORMAT OFF ENTMAP ON -
HEAD "<TITLE>Department Report</TITLE> -
<STYLE type='text/css'> -
<!-- BODY {background: #AACCC6} --> -
</STYLE>" –
 BODY "TEXT='#FF00Ff'" –
 TABLE "WIDTH='90%' BORDER='5'"
SPOOL TimeTable.html
SELECT DISTINCT C.codeCours, T.jourCoursDate,C.VOLUMEH FROM Cours C
JOIN Typehoraire T
ON C.codeCours= T.crsCodeCours
JOIN Jourcours J
ON J.dateJourCours=T.jourCoursDate
JOIN Coursdeclasse cls
ON T.crsCodeCours=cls.crsCodeCours
JOIN Classe Cl
ON cl.specialiteNomSpec=cls.classSpecialiteNomspec
JOIN Etudiantdeclasse et 
on cls.crsCodeCours=et.COURCODECOURS
JOIN ETUDIANT pp 
ON pp.MATRICULE=et.ETUDIANTMATRICULE
WHERE  et.ETUDIANTMATRICULE=&Matricule AND PASSWORD=&Password;

3.) Ecrivons le script correspondant :

CREATE VIEW EmploiDeTemps AS
    SELECT DISTINCT T.jourCoursDate, C.codeCours
    FROM Cours C
        JOIN Typehoraire T
        ON C.codeCours= T.crsCodeCours
        JOIN Jourcours J
        ON J.dateJourCours=T.jourCoursDate
        JOIN Coursdeclasse cls
        ON  T.crsCodeCours=cls.crsCodeCours
        JOIN Classe Cl
        ON cl.specialiteNomSpec=cls.classSpecialiteNomspec
    ORDER BY T.jourCoursDate;
  
4.)Ecrivons le script correspondant :

alter table etudiant add passwort varchar(50)
update etudiant set password = ora_hash(matricule);

alter table enseignant add passwort varchar(50)
update enseignant set password = ora_hash(matricule);



