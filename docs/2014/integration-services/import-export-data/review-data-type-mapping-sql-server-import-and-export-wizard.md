---
title: Vérifier le mappage de type de données (Assistant Importation et Exportation SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.impexpwizard.reviewissues.f1
ms.assetid: 0625c4f9-b8ff-4593-b884-39398b9d43af
caps.latest.revision: 18
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cbfaab44f1b7c40a912eec0c6c6cef8a6b00c51f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37158910"
---
# <a name="review-data-type-mapping-sql-server-import-and-export-wizard"></a>Vérifier le mappage de type de données (Assistant Importation et Exportation SQL Server)
  Utilisez le **vérifier le mappage de Type de données** page pour consulter des informations détaillées sur les conversions de type de données que l’Assistant doit effectuer pour que les données sources soient compatibles avec la destination. Ces informations incluent des aides visuelles permettant de différencier les conversions qui sont censées aboutir de celles qui sont susceptibles de provoquer des erreurs ou des troncations. Pour chaque conversion, vous pouvez choisir d'accepter ou non la conversion que l'Assistant suggère. Qui plus est, vous pouvez spécifier comment gérer les erreurs.  
  
 Pour en savoir plus sur cet Assistant, consultez [SQL Server Assistant Importation et exportation](import-and-export-data-with-the-sql-server-import-and-export-wizard.md). Pour en savoir plus sur les options de démarrage de l’Assistant et sur les autorisations requises pour exécuter l’Assistant avec succès, consultez [exécuter le SQL Server Assistant Importation et exportation](start-the-sql-server-import-and-export-wizard.md).  
  
 L’objectif de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Importation et exportation consiste à copier des données à partir d’une source vers une destination. L'Assistant peut également créer une base de données de destination et des tables de destination à votre intention. Toutefois, si vous devez copier plusieurs tables ou bases de données, ou autres types d'objets de bases de données, vous devez plutôt utiliser l'Assistant Copie de base de données. Pour plus d'informations, consultez [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="options"></a>Options  
 La page **Vérifier le mappage de type de données** comporte une liste **Table** , une liste **Mappage de type de données** et des options de gestion des erreurs.  
  
### <a name="table-list"></a>Liste Table  
 La partie supérieure de la **vérifier le mappage de Type de données** page est un **Table** liste qui répertorie les tables à transférer à partir de la source vers la destination. Le tableau suivant décrit les colonnes figurant dans cette liste.  
  
|colonne|Description|  
|------------|-----------------|  
|Icône de la source|Indique la probabilité de réussite des conversions de types de données :<br /><br /> Une icône représentant une coche verte indique que l'Assistant prévoit la réussite de toutes les conversions de types de données de cette table.<br /><br /> Une icône d'avertissement jaune indique que vous devrez examiner les différentes conversions qui seront effectuées par l'Assistant. Pour ce faire, sélectionnez la table, puis examinez les conversions correspondant aux différentes colonnes dans la liste **Mappage de type de données** .<br /><br /> Une icône d'erreur rouge indique que l'Assistant n'est pas en mesure d'effectuer de manière fiable certaines conversions pour cette table.|  
|**Source**|Affiche le nom de la table source.|  
|Icône de la destination|Indique si la destination existe déjà ou si elle doit être créée par l'Assistant :<br /><br /> Une icône de table indique que la destination est une table existante.<br /><br /> Une icône de table comportant un rayon de soleil indique que la destination est une nouvelle table qui sera créée par l'Assistant.|  
|**Destination**|Affiche le nom de la table de destination.|  
  
 Pour afficher les informations de conversion d’une table individuelle, sélectionnez une table dans ce **Table** grille. Les informations de conversion de la table sélectionnée apparaissent dans les colonnes, dans la partie inférieure **Grille de mappage des types de données** de la page.  
  
### <a name="data-type-mapping-list"></a>Liste Mappage de type de données  
 La partie inférieure de la **vérifier le mappage de Type de données** page est la **mappage de type de données** liste. Cette grille inclut des informations de conversion détaillées concernant les colonnes de la table sélectionnée dans la liste **Table** . Le tableau suivant décrit les colonnes figurant dans cette liste.  
  
|colonne|Description|  
|------------|-----------------|  
|Icône de conversion|Indique la probabilité de réussite des conversions de types de données :<br /><br /> Une icône représentant une coche verte indique que l'Assistant prévoit la réussite de la conversion des types de données de cette colonne.<br /><br /> Une icône d'avertissement jaune indique que vous devrez examiner la conversion qui sera effectuée par l'Assistant. Pour vérifier la conversion, double-cliquez sur la colonne afin d’afficher la boîte de dialogue **Détails de la conversion de colonne** .<br /><br /> Une icône d'erreur rouge indique que l'Assistant n'est pas en mesure d'effectuer la conversion de manière fiable.|  
|**Colonne source**|Affiche le nom de la colonne source.|  
|**Type de source**|Affiche le type de données de la colonne source.|  
|**Colonne de destination**|Affiche le nom de la colonne de destination.|  
|**Type de destination**|Affiche le type de données de la colonne de destination.|  
|**Convert**|Spécifiez si la conversion planifiée doit se poursuivre :<br /><br /> Activez la case à cocher pour que l'Assistant poursuive la conversion planifiée.<br /><br /> Désactivez la case à cocher pour annuler la conversion des types de données.|  
|**En cas d’erreur**|Spécifiez comment l'Assistant gère les erreurs :<br /><br /> Utilisez le **en cas d’erreur (global)** paramètre.<br /><br /> Échouez avec une erreur et arrêtez le processus d'importation ou d'exportation.<br /><br /> Ignorez l'erreur.|  
|**En cas de troncation**|Spécifiez comment l'Assistant gère les troncations :<br /><br /> Utilisez le **en cas de troncation (global)** paramètre.<br /><br /> Échouez avec une erreur et arrêtez le processus d'importation ou d'exportation<br /><br /> Ignorez la troncation.|  
  
 Pour afficher des informations détaillées sur la conversion d'une colonne de données spécifique, double-cliquez sur une ligne dans la liste. La boîte de dialogue **Détails de la conversion de colonne** s'ouvre et affiche des informations de conversion plus détaillées pour la colonne.  
  
### <a name="error-handling-options"></a>Options de gestion des erreurs  
 **En cas d’erreur (global)**  
 Spécifiez comment l'Assistant gère les erreurs :  
  
-   Échouez avec une erreur et arrêtez le processus d'importation ou d'exportation.  
  
-   Ignorez l'erreur et poursuivez le processus d'importation ou d'exportation.  
  
 Ce paramètre s'applique à toutes les conversions pour lesquelles l'option **Utiliser Global** est sélectionnée dans la colonne **En cas d'erreur** de la liste **Mappage de type de données** .  
  
 **En cas de troncation (global)**  
 Spécifiez comment l'Assistant gère les troncations :  
  
-   Échouez avec une erreur et arrêtez le processus d'importation ou d'exportation.  
  
-   Ignorez la troncation et poursuivez le processus d'importation ou d'exportation.  
  
 Ce paramètre s'applique à toutes les conversions pour lesquelles l'option **Utiliser Global** est sélectionnée dans la colonne **En cas de troncation** de la liste **Mappage de type de données** .  
  
  
