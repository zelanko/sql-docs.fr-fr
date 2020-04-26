---
title: 'Tâche 2 : mappage des colonnes Excel aux domaines DQS | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: f347cc92-950f-4021-b7af-393640dfe821
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 29d45e06dcd3e67af3abbc6b356d44877e40f46b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "65484707"
---
# <a name="task-2-mapping-excel-columns-to-dqs-domains"></a>Tâche 2 : Mappage de colonnes d’Excel aux domaines DQS
    
1.  Dans la page **Mapper** , sélectionnez **Fichier Excel** pour **Source de données**.  
  
2.  Cliquez sur **Parcourir**, sélectionnez **Suppliers. xlsx**, puis cliquez sur **ouvrir**.  
  
3.  Sélectionnez **IncomingSuppliers $** pour la **feuille de calcul**.  
  
4.  Mappez les colonnes comme indiqué dans le tableau suivant et dans la capture d'écran. Lorsque vous créez des mappages pour le domaine d' **État** , cliquez sur le bouton **Ajouter un mappage de colonnes** dans la barre d’outils située juste au-dessus de la liste.  
  
    > [!TIP]  
    >  Vous n’utilisez pas la colonne/le domaine de l' **ID de fournisseur** pour le nettoyage. Vous utiliserez le domaine **ID du fournisseur** ultérieurement dans l’activité de correspondance.  
  
    |Colonne Excel|Domaine DQS|  
    |------------------|----------------|  
    |Nom du fournisseur|Nom du fournisseur|  
    |ContactEmailAddress|E-mail du contact|  
    |Adresse|Adresse|  
    |City|City|  
    |State|State|  
    |Pays (cliquez sur **+ (ajouter un mappage de colonnes)** barre d’outils pour ajouter une ligne)|Country|  
    |Code postal|Zip|  
  
     ![Mappages des colonnes d'Excel aux domaines](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-01.jpg "Mappages des colonnes d'Excel aux domaines")  
  
5.  Comme vous avez mappé tous les domaines individuels dans le domaine composite **validation d’adresse** , le domaine composite participe automatiquement au processus de nettoyage. Cliquez sur le bouton **Afficher/sélectionner des domaines composites** pour voir que le domaine composite **validation d’adresse** est sélectionné automatiquement, puis cliquez sur **OK**.  
  
     ![Boîte de dialogue Afficher/Sélectionner des domaines composites](../../2014/tutorials/media/et-mappingexcelcolumnstodqsdomains-02.jpg "Boîte de dialogue Afficher/Sélectionner des domaines composites")  
  
6.  Cliquez sur **suivant** pour basculer vers la page **nettoyer** .  
  
## <a name="next-step"></a>étape suivante  
 [Tâche 3 : Nettoyage des données dans la base de connaissances Fournisseurs](../../2014/tutorials/task-3-cleansing-data-against-the-suppliers-knowledge-base.md)  
  
  
