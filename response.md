Nom: Lban Sondosse
GRP: B

Question 1 
Pourquoi utilise-t-on un forward quand le login échoue, mais un sendRedirect quand il réussit ?

Réponse :

Lorsqu'un login échoue, on utilise forward pour transmettre directement la requête à la JSP en conservant les attributs, notamment le message d'erreur et le nom d'utilisateur saisi.

Lorsqu'un login réussit, on utilise sendRedirect pour envoyer le navigateur vers /dashboard. Cela crée une nouvelle requête et évite de renvoyer le formulaire de connexion lors d'un rafraîchissement.

Question 2 
Que se passe-t-il si l'utilisateur appuie sur F5 juste après avoir ajouté un produit ?

Réponse :

a) Si doPost fait un forward vers la liste, le navigateur peut renvoyer la même requête POST. Le produit risque donc d'être ajouté une deuxième fois.

b) Si doPost fait un redirect, le navigateur effectue une nouvelle requête GET vers la liste. Le rafraîchissement ne répète donc pas l'ajout.

Ce mécanisme s'appelle le pattern PRG (Post/Redirect/Get).

Question 3 
Que se passe-t-il avec ${produit.nom} et <c:out> si le nom est <script>alert(1)</script> ?

Réponse :

${produit.nom} affiche directement la valeur et peut interpréter le contenu HTML dans la page. Cela peut provoquer une attaque XSS.

<c:out value="${produit.nom}"/> échappe les caractères HTML spéciaux et affiche le texte sans exécuter le script.

Il faut donc privilégier <c:out> pour afficher les données saisies par les utilisateurs.

Question 4 
Quel est l'avantage du filtre par rapport à la vérification dans chaque servlet ? Citez deux autres usages classiques.

Réponse :

Le filtre permet de centraliser le contrôle d'accès dans une seule classe. Il évite de répéter le même code dans plusieurs servlets et facilite la maintenance de l'application.

Deux autres usages classiques des filtres sont :
1. Vérifier ou modifier l'encodage des requêtes (UTF-8).
2. Enregistrer les requêtes dans des journaux (logs) pour surveiller l'application.
