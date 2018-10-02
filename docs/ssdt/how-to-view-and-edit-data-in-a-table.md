---
title: 'Procédure : afficher et modifier des données dans une table | Microsoft Docs'
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- SQL.DATA.TOOLS.QUERYRESULTS.F1
- sql.data.tools.queryresults.executequerydeletingrow
ms.assetid: bb67ce83-a87a-4e14-84cd-9a5930fe74c8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 543611c2e5c327d50ea7155969a670ac4a0e836e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47685429"
---
# <a name="how-to-view-and-edit-data-in-a-table"></a>Procédure : afficher et modifier des données dans une table
Vous pouvez consulter, modifier et supprimer des données d'une table existante à l'aide de l'Éditeur de données visuel.  
  
> [!WARNING]  
> Les procédures suivantes utilisent les entités créées dans les procédures précédentes de la section [Développement d’une base de données connectée](../ssdt/connected-database-development.md).  
  
### <a name="to-edit-data-in-a-table-visually-using-the-data-editor"></a>Pour modifier des données dans une table visuellement à l'aide de l'Éditeur de données  
  
1.  Dans l’**Explorateur d'objets SQL Server**, cliquez avec le bouton droit sur **Produit** et sélectionnez **Afficher les données**.  
  
2.  L'Éditeur de données démarre. Notez les lignes ajoutées à la table dans les procédures précédentes.  
  
3.  Dans l’Explorateur d'objets SQL Server, cliquez avec le bouton droit sur **Fruits** et sélectionnez **Afficher les données**.  
  
4.  Dans l'Éditeur de données, tapez **1** pour **Id** et **True** pour **Perishable**, puis appuyez sur Entrée ou sur Tabulation pour déplacer le focus de la nouvelle ligne afin de la valider dans la base de données.  
  
5.  Répétez l'étape ci-dessus pour entrer **2**, **False** et **3**, **False** dans la table.  
  
    Notez que lorsque vous modifiez une ligne, vous pouvez toujours annuler les modifications apportées à une cellule en appuyant sur Échap.  
  
6.  Pour afficher vos modifications sous la forme d'un script, cliquez sur le bouton **Script** dans la barre d'outils. Vous pouvez aussi utiliser le bouton **Générer un script dans un fichier** pour les enregistrer dans un fichier de script .sql à exécuter ultérieurement.  
  
7.  Dans l’**Explorateur d'objets SQL Server**, cliquez avec le bouton droit sur **Trade** et sélectionnez **Nouvelle requête**. Dans l'éditeur, tapez `select * from dbo.PerishableFruits` et cliquez sur le bouton **Exécuter la requête`PerishableFruits` pour revenir aux données représentées par l'affichage** .  
  
