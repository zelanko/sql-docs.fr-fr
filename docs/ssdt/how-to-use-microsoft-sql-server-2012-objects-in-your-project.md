---
title: Objets SQL Server 2012 dans votre projet
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
ms.assetid: 9baf122f-cf22-4860-98db-ef782cd972fc
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: 69c68812e169d2831ffde71d2b21f9af8f418600
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81486790"
---
# <a name="how-to-use-microsoft-sql-server-2012-objects-in-your-project"></a>Procédure : utiliser des objets Microsoft SQL Server 2012 dans votre projet

Dans cet exemple, vous ajouterez un objet séquence à un projet de base de données ciblant Microsoft SQL Server 2012.  
  
Des séquences sont introduites dans Microsoft SQL Server 2012. Une séquence est un objet lié par schéma défini par l'utilisateur qui génère une séquence de valeurs numériques d'après la spécification avec laquelle la séquence a été créée. La séquence de valeurs numériques est générée dans un ordre croissant ou décroissant à un intervalle défini et peut effectuer un cycle (répétition) selon la demande.  Pour plus d'informations sur les objets séquence, consultez [Numéros de séquence](../relational-databases/sequence-numbers/sequence-numbers.md). Pour plus d’informations sur les nouveautés concernant Microsoft SQL Server 2012, consultez [Nouveautés de SQL Server 2012 ](https://msdn.microsoft.com/library/bb500435(SQL.110).aspx).  
  
> [!WARNING]  
> Les procédures suivantes utilisent les entités créées dans les procédures précédentes des sections [Développement de base de données connectée](../ssdt/connected-database-development.md) et [Développement de base de données hors connexion orienté projet](../ssdt/project-oriented-offline-database-development.md).  
  
### <a name="to-add-a-new-sequence-object-to-your-project"></a>Pour ajouter un nouvel objet séquence à votre projet  
  
1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le projet de base de données **TradeDev**, sélectionnez **Ajouter**, puis **Nouvel élément**.  
  
2.  Cliquez sur **Programmabilité** dans le volet gauche, et sélectionnez **Séquence**. Cliquez sur **Ajouter** pour ajouter le nouvel objet au projet.  
  
3.  Remplacez le code par défaut par ce qui suit.  
  
    ```  
    CREATE SEQUENCE [dbo].[Seq1]  
    AS INT  
    START WITH 1  
    INCREMENT BY 1  
    MAXVALUE 1000  
    NO CYCLE  
    CACHE 10  
    ```  
  
4.  Si la plateforme cible de votre projet n’est pas définie sur Microsoft SQL Server 2012, la **Liste d’erreurs** affichera une erreur de syntaxe pour l’instruction `CREATE SEQUENCE`. Pour remédier à ce problème, consultez la rubrique [Procédure : modifier la plateforme cible et publier un projet de base de données](../ssdt/how-to-change-target-platform-and-publish-a-database-project.md) pour modifier la plateforme cible en conséquence.  
  
5.  Consultez la rubrique [Procédure : modifier la plateforme cible et publier un projet de base de données](../ssdt/how-to-change-target-platform-and-publish-a-database-project.md) pour publier le projet dans une base de données de votre serveur Microsoft SQL Server 2012 connecté.  
  
### <a name="to-use-the-new-sequence-object"></a>Pour utiliser le nouvel objet séquence  
  
1.  Dans l’Explorateur d'objets SQL Server, cliquez avec le bouton droit sur la base de données publiée dans la procédure précédente, puis sélectionnez **Nouvelle requête**.  
  
2.  Collez le code suivant dans la fenêtre de requête.  
  
    ```  
    DECLARE @counter INT  
    SET @counter=0  
    WHILE @counter<10  
    BEGIN  
        SET @counter = @counter +1  
         INSERT dbo.Products (Id, Name, CustomerId) VALUES (NEXT VALUE FOR dbo.Seq1, 'ProductItem'+cast(@counter as varchar), 1)  
    END   
    GO  
    ```  
  
3.  Cliquez sur le bouton **Exécuter la requête**.  
  
4.  Dans l'**Explorateur d'objets SQL Server**, accédez à la table **Produits** de la base de données. Cliquez avec le bouton droit et sélectionnez **Afficher les données** pour examiner les nouvelles lignes ajoutées.  
  
