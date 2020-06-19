---
title: Extraire des données à l’aide de la source OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- extracting data [Integration Services]
- sources [Integration Services], OLE DB
- OLE DB source [Integration Services]
ms.assetid: 4ca6eeb5-b60e-4b81-86dd-0674be8ae8d8
author: janinezhang
ms.author: janinez
ms.openlocfilehash: aa6e88fec83b6d70a7f96f91ea09b4fcd6ad13c9
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84915679"
---
# <a name="extract-data-by-using-the-ole-db-source"></a>Extraire des données à l'aide de la source OLE DB
  Pour pouvoir ajouter et configurer une source OLE DB, le package doit inclure au moins une tâche de flux de données.  
  
### <a name="to-extract-data-using-an-ole-db-source"></a>Pour extraire des données à l'aide d'une source OLE DB  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l'onglet **Flux de données** , puis dans la **Boîte à outils**, faites glisser la source OLE DB sur l'aire de conception.  
  
4.  Double-cliquez sur la source OLE DB.  
  
5.  Dans la boîte de dialogue **Éditeur de source OLE DB** , dans la page **Gestionnaire de connexions** , sélectionnez un gestionnaire de connexions OLE DB existant ou cliquez sur **Nouveau** pour créer un gestionnaire de connexions. Pour plus d’informations, consultez [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).  
  
6.  Sélectionnez la méthode d'accès aux données :  
  
    -   **Table ou vue** Sélectionnez une table ou une vue dans la base de données à laquelle le gestionnaire de connexions OLE DB se connecte.  
  
    -   **Variable de nom de table ou de vue** Sélectionnez la variable définie par l’utilisateur contenant le nom d’une table ou d’une vue dans la base de données à laquelle le gestionnaire de connexions OLE DB se connecte.  
  
    -   **Commande SQL** Tapez une commande SQL ou cliquez sur **Générer la requête** pour écrire une commande SQL à l’aide du **Générateur de requêtes**.  
  
        > [!NOTE]  
        >  La commande peut inclure des paramètres. Pour plus d’informations, consultez [Mapper des paramètres de requête à des variables dans un composant de flux de données](map-query-parameters-to-variables-in-a-data-flow-component.md).  
  
    -   **Commande SQL à partir d’une variable** Sélectionnez la variable définie par l’utilisateur contenant la commande SQL.  
  
        > [!NOTE]  
        >  Les variables doivent être définies dans la même étendue que la tâche de flux de données qui contient la source OLE DB ou dans la même étendue que le package. Par ailleurs, les données de la variable doivent être de type string.  
  
7.  Pour mettre à jour le mappage entre les colonnes externes et les colonnes de sortie, cliquez sur **Colonnes** et sélectionnez des colonnes dans la liste **Colonne externe** .  
  
8.  Si vous le souhaitez, mettez à jour les noms des colonnes de sortie en modifiant des valeurs dans la liste **Colonne de sortie** .  
  
9. Pour configurer l'affichage des erreurs, cliquez sur **Sortie d'erreur**. Pour plus d’informations, consultez [Configurer une sortie d’erreur dans un composant de flux de données](../configure-an-error-output-in-a-data-flow-component.md).  
  
10. Vous pouvez cliquer sur **Aperçu** pour afficher jusqu’à 200 lignes de données extraites par la source OLE DB.  
  
11. Cliquez sur **OK**.  
  
12. Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Source OLE DB](ole-db-source.md)   
 [Transformations Integration Services](transformations/integration-services-transformations.md)   
 [Chemins Integration Services](integration-services-paths.md)   
 [tâche de flux de données](../control-flow/data-flow-task.md)  
  
  
