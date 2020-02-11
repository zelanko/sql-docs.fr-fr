---
title: Extraire des données à l’aide de la source ODBC | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 10f25703-49a2-4d45-abab-6b4da2a57ba5
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f8ecb517174c8cd8189ad2f7382c774df3545620
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62864946"
---
# <a name="extract-data-by-using-the-odbc-source"></a>Extraire des données à l'aide de la source ODBC
  Cette procédure explique comment extraire des données à l'aide d'une source ODBC. Pour pouvoir ajouter et configurer une source ODBC, le package doit inclure au moins une tâche de flux de données.  
  
### <a name="to-extract-data-using-an-odbc-source"></a>Pour extraire des données à l'aide d'une source ODBC  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], ouvrez le package [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] souhaité.  
  
2.  Cliquez sur l'onglet **Flux de données** , puis dans la **Boîte à outils**, faites glisser la source ODBC sur l'aire de conception.  
  
3.  Double-cliquez sur la source ODBC.  
  
4.  Dans la boîte de dialogue **Éditeur de source ODBC** , dans la page **Gestionnaire de connexions** , sélectionnez un gestionnaire de connexions ODBC existant ou cliquez sur **Nouveau** pour créer un gestionnaire de connexions.  
  
5.  Sélectionnez la méthode d'accès aux données.  
  
    -   **Nom de la table**: sélectionnez une table ou une vue dans la base de données ou tapez une expression régulière pour identifier la table à laquelle le gestionnaire de connexions ODBC se connecte.  
  
         Cette liste contient les 1 000 premières tables uniquement. Si votre base de données contient plus de 1 000 tables, vous pouvez taper le début du nom d'une table ou utiliser le caractère générique (*) pour entrer une partie du nom afin d'afficher la table ou les tables que vous souhaitez utiliser.  
  
    -   **Commande SQL**: tapez une commande SQL ou cliquez sur **Parcourir** pour charger la requête SQL à partir d'un fichier texte.  
  
6.  Vous pouvez cliquer sur **Aperçu** pour afficher jusqu'à 200 lignes de données extraites par la source ODBC.  
  
7.  Pour mettre à jour le mappage entre les colonnes externes et les colonnes de sortie, cliquez sur **Colonnes** et sélectionnez des colonnes dans la liste **Colonne externe** .  
  
8.  Si nécessaire, mettez à jour les noms des colonnes de sortie en modifiant les valeurs dans la liste **Colonne de sortie** .  
  
9. Pour configurer l'affichage des erreurs, cliquez sur **Sortie d'erreur**.  
  
10. Cliquez sur **OK**.  
  
11. Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de source ODBC &#40;page Gestionnaire de connexions&#41;](../odbc-source-editor-connection-manager-page.md)   
 [Éditeur de source ODBC &#40;page Colonnes&#41;](../odbc-source-editor-columns-page.md)   
 [Éditeur de source ODBC &#40;page Sortie d’erreur&#41;](../odbc-source-editor-error-output-page.md)  
  
  
