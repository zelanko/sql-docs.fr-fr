---
title: Boutons de commande de carnet d’adresses | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- address book application scenario [ADO], command buttons
- RDS scenarios [ADO], command buttons
ms.assetid: 80676831-6488-4dad-a558-c47c52256a22
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d1aa5b628bec9399374b94a2cd78090207bf09b7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67922984"
---
# <a name="address-book-command-buttons"></a>Boutons de commande de l’application Carnet d’adresses
L’application de carnet d’adresses comprend les boutons de commande suivants :  
  
-   Un **trouver** pour envoyer une requête à la base de données.  
  
-   Un **effacer** bouton pour effacer les zones de texte avant de commencer une nouvelle recherche.  
  
-   Un **profil de mise à jour** bouton pour enregistrer les modifications dans un enregistrement d’employé.  
  
-   Un **annuler les modifications** bouton pour ignorer les modifications.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="find-button"></a>Bouton Rechercher  
 En cliquant sur le **trouver** bouton Active la procédure Sub Find_OnClick de VBScript qui génère et envoie la requête SQL. Cliquez sur ce bouton remplit la grille de données.  
  
## <a name="building-the-sql-query"></a>Création de la requête SQL  
 La première partie de la procédure Sub « Find_OnClick » génère la requête SQL, une expression à la fois, en ajoutant des chaînes de texte à une instruction SQL SELECT globale. Il commence en définissant la variable `myQuery` pour une instruction SQL SELECT qui demande de toutes les lignes de données à partir de la table de source de données. Ensuite, la procédure Sub analyse chacune des quatre zones de texte sur la page.  
  
 Étant donné que le programme utilise le mot `like` dans la création des instructions SQL, les requêtes sont des recherches de sous-chaînes plutôt que des correspondances exactes.  
  
 Par exemple, si le **nom** boîte contenue l’entrée « Berge » et le **titre** boîte contenue l’entrée « Program Manager », l’instruction SQL (valeur de `myQuery`) lit :  
  
```sql
Select FirstName, LastName, Title, Email, Building, Room, Phone from Employee where lastname like 'Berge%' and title like 'Program Manager%'  
```  
  
 Si la requête a réussi, toutes les personnes ayant un nom contenant le texte « Berge » (par exemple, Berge ou Berger) et avec un titre qui contient les mots « Responsable de programme » (par exemple, responsable de programme, des Technologies avancées) sont affichés dans la grille de données HTML.  
  
## <a name="preparing-and-sending-the-query"></a>Préparation et l’envoi de la requête  
 La dernière partie de la procédure Sub « Find_OnClick » se compose de deux instructions. La première instruction affecte le [SQL](../../../ado/reference/rds-api/sql-property.md) propriété de la [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) à l’objet. La deuxième instruction provoque la **RDS. DataControl** objet (`DC1`) pour interroger la base de données et afficher les nouveaux résultats de la requête dans la grille.  
  
```vb
Sub Find_OnClick  
   '...  
   DC1.SQL = myQuery  
   DC1.Refresh  
End Sub  
```  
  
## <a name="update-profile-button"></a>Bouton de mise à jour le profil  
 En cliquant sur le **profil de mise à jour** bouton Active la procédure Sub Update_OnClick de VBScript qui exécute le [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) l’objet (`DC1`) [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) et [Actualiser](../../../ado/reference/rds-api/refresh-method-rds.md) méthodes.  
  
```vb
Sub Update_OnClick  
   DC1.SubmitChanges  
   DC1.Refresh  
End Sub  
```  
  
 Lorsque `DC1.SubmitChanges` s’exécute, le Service de données distant regroupe toutes les informations de mise à jour et les envoie au serveur via HTTP. La mise à jour est tout ou rien ; Si une partie de la mise à jour échoue, aucune des modifications est effectuée et un message d’état est retourné. `DC1.Refresh` n’est pas nécessaire après **SubmitChanges** avec le Service de données distant, mais il garantit des données actualisées.  
  
## <a name="cancel-changes-button"></a>Modifications bouton Annuler  
 En cliquant sur **annuler les modifications** Active la procédure Sub Cancel_OnClick de VBScript qui exécute le [RDS. DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) l’objet (`DC1)` [CancelUpdate](../../../ado/reference/rds-api/cancelupdate-method-rds.md) (méthode).  
  
```vb
Sub Cancel_OnClick  
   DC1.CancelUpdate  
End Sub  
```  
  
 Lorsque `DC1.CancelUpdate` s’exécute, il rejette toutes les modifications qu’un utilisateur a apportées à un enregistrement d’employé dans la grille de données depuis la dernière requête ou mise à jour. Il restaure les valeurs d’origine.  
  
## <a name="see-also"></a>Voir aussi  
 [Boutons de Navigation de carnet d’adresses](../../../ado/guide/remote-data-service/address-book-navigation-buttons.md)   
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)


