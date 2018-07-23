---
title: 'Guide pratique : Déboguer des procédures stockées | Microsoft Docs'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- SQL.DATA.TOOLS.EXECUTESTOREDPROCEDURE.DIALOG
ms.assetid: e3c8707f-0f6b-4265-8a5a-81f079330b52
caps.latest.revision: 19
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f2cae581128fc80d2dd447998d3e49ae5e0d8866
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39087391"
---
# <a name="how-to-debug-stored-procedures"></a>Procédure : déboguer des procédures stockées
Le débogueur Transact\-SQL permet de déboguer interactivement des procédures stockées en affichant la pile des appels SQL, les variables locales et les paramètres de la procédure stockée SQL. Comme pour le débogage dans d’autres langages de programmation, il est possible d’afficher et modifier les variables locales et les paramètres, d’afficher les variables globales et de contrôler et gérer les points d’arrêt lors du débogage du script Transact\-SQL.  
  
Cet exemple explique comment créer et déboguer une procédure stockée Transact\-SQL en effectuant un pas à pas détaillé.  
  
> [!WARNING]  
> La procédure suivante utilise les entités créées dans les procédures des sections [Développement de base de données connectée](../ssdt/connected-database-development.md) et [Développement de base de données hors connexion orienté projet](../ssdt/project-oriented-offline-database-development.md).  
  
### <a name="to-debug-stored-procedures"></a>Pour déboguer des procédures stockées  
  
1.  Dans **l’Explorateur de solutions**, cliquez avec le bouton droit sur le projet **TradeDev** et sélectionnez **Ajouter**, puis **Procédure stockée**. Nommez cette nouvelle procédure stockée **AddProduct** et cliquez sur **Ajouter**.  
  
2.  Collez le code suivant dans la procédure stockée.  
  
    ```  
    CREATE PROCEDURE [dbo].[AddProduct]  
    @id int,  
    @name nvarchar(128)  
    AS  
    INSERT INTO [dbo].[Product] (Id, Name) VALUES (@id, @name)  
    ```  
  
3.  Appuyez sur F5 pour générer et déployer le projet.  
  
4.  Sous le nœud **Local** de l’Explorateur d’objets SQL Server, cliquez avec le bouton droit sur la base de données **TradeDev**, puis sélectionnez **Nouvelle requête**.  
  
5.  Collez le code suivant dans la fenêtre de requête.  
  
    ```  
    EXEC [dbo].[AddProduct] 50, N'Contoso';  
    GO  
    ```  
  
6.  Cliquez sur la marge de la fenêtre de gauche pour ajouter un point d'arrêt à l'instruction `EXEC`.  
  
7.  Cliquez sur la flèche déroulante vers le bas du bouton représentant une flèche verte dans la barre d’outils de l’Éditeur Transact\-SQL et sélectionnez **Exécuter avec le débogueur** pour exécuter la requête en mode débogage.  
  
8.  Vous pouvez également lancer le débogage à partir de l’Explorateur d’objets SQL Server. Cliquez avec le bouton droit sur la procédure stockée **AddProduct** (sous **Local** -> **base de données TradeDev** -> **Programmabilité** -> **Procédures stockées**). Sélectionnez **Déboguer la procédure…**. Si l’objet exige des paramètres, la boîte de dialogue **Déboguer la procédure** affiche une table comportant une ligne par paramètre. Chaque ligne dans la table contient une colonne pour le nom du paramètre, et une pour la valeur de ce paramètre. Entrez les valeurs pour chaque paramètre et cliquez sur OK.  
  
9. Vérifiez que la fenêtre **Variables locales** est ouverte. Si ce n’est pas le cas, cliquez sur le menu **Déboguer**, sélectionnez **Fenêtres** et **Variables locales**.  
  
10. Appuyez sur F11 pour exécuter un pas à pas détaillé de la requête. Vous remarquerez que les paramètres de la procédure stockée et leurs valeurs respectives s’affichent dans la fenêtre **Variables locales**. Vous pouvez aussi placer le curseur sur le paramètre `@name` de la clause `INSERT` pour voir la valeur **Contoso** qui lui est affectée.  
  
11. Cliquez sur **Contoso** dans la zone de texte. Tapez **Fabrikam** et appuyez sur ENTRÉE pour modifier la valeur de la variable `name` lors du débogage. Vous pouvez également modifier sa valeur dans la fenêtre **Variables locales**. Remarquez que la valeur du paramètre s'affiche désormais en rouge, ce qui indique qu'elle a changé.  
  
12. Appuyez sur F10 pour exécuter un pas à pas détaillé du code restant.  
  
13. Dans l’Explorateur d’objets SQL Server, actualisez le nœud de base de données **TradeDev** pour afficher le nouveau contenu dans la Vue de données de la table **Product**.  
  
14. Sous le nœud **Local** de l’Explorateur d’objets SQL Server, localisez la table **Product** de la base de données **TradeDev**.  
  
15. Cliquez avec le bouton droit sur la table **Product** et sélectionnez **Afficher les données**. Vous pouvez remarquer que la nouvelle ligne a été ajoutée à la table.  
  
