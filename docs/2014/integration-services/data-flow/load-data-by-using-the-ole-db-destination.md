---
title: Charger des données à l’aide de la destination OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- loading data
- OLE DB destination [Integration Services]
- destinations [Integration Services], OLE DB
ms.assetid: 78899498-725e-4300-a7af-f983f4ea384b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 865ff640cb64fe212afa5ece8bbdaa7f0be4a14c
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52749505"
---
# <a name="load-data-by-using-the-ole-db-destination"></a>Charger des données à l'aide de la destination OLE DB
  Pour pouvoir ajouter et configurer une destination OLE DB, le package doit inclure au moins une tâche de flux de données et une source.  
  
### <a name="to-load-data-using-an-ole-db-destination"></a>Pour charger des données à l'aide d'une destination OLE DB  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de données** puis, dans la **Boîte à outils**, faites glisser la destination OLE DB vers l’aire de conception.  
  
4.  Connectez la destination OLE DB au flux de données en faisant glisser le connecteur à partir d'une source de données ou d'une transformation précédente vers la destination.  
  
5.  Double-cliquez sur la destination OLE DB.  
  
6.  Dans la boîte de dialogue **Éditeur de destination OLE DB** , dans la page **Gestionnaire de connexions** , sélectionnez un gestionnaire de connexions OLE DB existant ou cliquez sur **Nouveau** pour créer un gestionnaire de connexions. Pour plus d’informations, consultez [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).  
  
7.  Sélectionnez la méthode d'accès aux données :  
  
    -   **Table ou vue** : sélectionnez une table ou une vue dans la base de données qui contient les données.  
  
    -   **Table ou vue - chargement rapide** sélectionnez une table ou vue dans la base de données qui contient les données, puis définissez les options de chargement rapide : **Conserver l’identité**, **conserver les valeurs null**, **Table lock**, **contrainte de validation**, **lignes par lot**, ou **maximale taille de validation d’insertion**.  
  
    -   **Variable de nom de table ou de vue** : sélectionnez la variable définie par l’utilisateur qui contient le nom d’une table ou d’une vue dans la base de données.  
  
    -   **Variable de nom de table ou de vue - chargement rapide** : sélectionnez une variable définie par l’utilisateur qui contient le nom d’une table ou d’une vue dans la base de données qui contient les données, puis définissez les options de chargement rapide.  
  
    -   **Commande SQL** : tapez une commande SQL ou cliquez sur **Générer la requête** pour écrire une commande SQL à l’aide du **Générateur de requêtes**.  
  
8.  Cliquez sur **Mappages** , puis mappez les colonnes de la liste **Colonnes d'entrée disponibles** aux colonnes de la liste **Colonnes de destination disponibles** en faisant glisser les colonnes d'une liste à l'autre.  
  
    > [!NOTE]  
    >  La destination OLE DB mappe automatiquement les colonnes portant le même nom.  
  
9. Pour configurer l'affichage des erreurs, cliquez sur **Sortie d'erreur**. Pour plus d’informations, consultez [Configurer une sortie d’erreur dans un composant de flux de données](../configure-an-error-output-in-a-data-flow-component.md).  
  
10. Cliquez sur **OK**.  
  
11. Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Destination OLE DB](ole-db-destination.md)   
 [Transformations Integration Services](transformations/integration-services-transformations.md)   
 [Chemins d'accès d'Integration Services](integration-services-paths.md)   
 [tâche de flux de données](../control-flow/data-flow-task.md)  
  
  
