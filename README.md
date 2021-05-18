# Πληροφοριακά Συστήματα - Εργασία 1

## 0. Σύδεση με τη βάση InfoSys και εισαγωγή του αρχείου students.json στο collection Students της ΒΔ InfoSYs

  Θα ξεκινήσουμε το image της mongodb σε docker container και στη συνέχεια θα αντιγράψουμε τα data στο container
   
  ![](images/image1.jpg)
  
  Κάνουμε import τα δεδομένα του students.json στο collection της βάσης InfoSys με την παρακάτω εντολή (Εδώ βγαίνει error επειδή υπάρχουν ήδη μέσα απο προηγούμενη άσκηση)
  
  docker exec -it mongodb mongoimport --db=InfoSys --collection=Students --file=students.json
  
  ![](images/image2.jpg)
   
  Για να σιγουρευτούμε ότι τα αρχεία βρίσκονται μέσα στο collection που θέλουμε, θα μπούμε στο mongoshell και θα εκτελέσουμε την εντολή db.Students.count()
  
  ![](images/image3.jpg)
  
 ## 1. Ερώτημα 1
  
  #### username_from_request = data['username']
  Δημιούργησα μια μεταβλητή με όνομα username_from_request στην οποία θα αποθηκεύεται το username που λαμβάνουμε από τον χρήστη. 
  
  #### users = list(students.find({'username': username_from_request }))
  Δημιούργησα μια μεταβλητή με όνομα users. Σε αυτήν θα αποθηκεύεται το αποτέλεσμα της find(), αν υπάρχει ήδη χρήστης με το ίδιο username. Σε διαφορετική περίπτωση η λίστα θα παραμένει άδεια. Εδώ πρέπει το αποτέλεσμα να μετατραπεί σε lιστα με την list(), επειδή η collection.find() μας επιστρέφει τον cursor του αντικειμένου. Το όρισμα {'username': username_from_request } ψάχνει μέσα στο collection για αρχεία με το username που έχουμε λάβει από τον χρήστη.
  
  #### if not users:
  Αν η λίστα μας είναι κενή τότε δεν υπάρχει κάποιος με αυτό το username και εκτελείται η παρακάτω εντολή. Αλλιώς αν η λίστα μας περιέχει το αρχείο που βρήκε η find() με το ίδιο username, δεν θα προστεθεί ο χρήστης, και θα εμπφανιστεί μήνυμα αποτυχίας.
    
  ####  Users.insert_one({'username': username_from_request ,'password': data['password']})
  Εισάγει τον χρήστη με το username και το password του στο collection με όνομα Users, το οποίο δημιουργείται αυτόματα με αυτή την εντολή.
  
  #### return Response(data['username'] + " was added to the MongoDB",status=200, mimetype='application/json')
  Προστέθηκε το status=200 για να δηλωθεί ότι το request εκτελέστηκε με επιτυχία.
  
  #### return Response("A user with the given username already exists",status=500, mimetype='application/json')
  Προστέθηκε το status=500 για να δηλωθεί ότι το request δεν εκτελέστηκε με επιτυχία.
    
  
