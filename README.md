# Πληροφοριακά Συστήματα - Εργασία 1

## 0. Σύδεση με τη βάση InfoSys και εισαγωγή του αρχείου students.json στο collection Students της ΒΔ InfoSYs

  Θα ξεκινήσουμε το image της mongodb σε docker container και στη συνέχεια θα αντιγράψουμε τα data στο container
   
  ![](images/image1.jpg)
  
  Κάνουμε import τα δεδομένα του students.json στο collection της βάσης InfoSys με την παρακάτω εντολή (Εδώ βγαίνει error επειδή υπάρχουν ήδη μέσα απο προηγούμενη άσκηση)
  
  docker exec -it mongodb mongoimport --db=InfoSys --collection=Students --file=students.json
  
  ![](images/image2.jpg)
   
  Για να σιγουρευτούμε ότι τα αρχεία βρίσκονται μέσα στο collection που θέλουμε, θα μπούμε στο mongoshell και θα εκτελέσουμε την εντολή db.Students.count()
  
  ![](images/image3.jpg)
  
  
