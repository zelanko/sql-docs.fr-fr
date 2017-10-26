---
title: "Récupérer et comprendre les données modifiées | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- incremental load [Integration Services],retrieving data
ms.assetid: af366697-6942-42bb-aea5-18fdef018965
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: caf66f974e832fcd1b27caf650d187942b3f19fe
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="retrieve-and-understand-the-change-data"></a>Récupérer et comprendre les données modifiées
  Dans le flux de données d’un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] qui effectue un chargement incrémentiel des données modifiées, la première tâche consiste à exécuter la requête qui récupère les données modifiées. Vous exécutez cette requête dans un composant source dans une tâche de flux de données. Vous pouvez ensuite utiliser des transformations et des destinations en aval pour appliquer les données modifiées à votre destination.  
  
> [!NOTE]  
>  La création d'une requête qui contient une fonction table est la troisième étape du processus de création d'un package qui effectue un chargement incrémentiel des données modifiées. Pour plus d’informations sur cette requête, consultez [Créer la fonction de récupération des données modifiées](../../integration-services/change-data-capture/create-the-function-to-retrieve-the-change-data.md). Pour obtenir une description du processus global de création d’un package qui effectue un chargement incrémentiel des données modifiées, consultez [Capture des données modifiées &#40;SSIS&#41;](../../integration-services/change-data-capture/change-data-capture-ssis.md).  
  
## <a name="adding-the-data-flow-task"></a>Ajout de la tâche de flux de données  
 Dans le flux de données du package, vous récupérez les données modifiées, vous séparez les lignes en fonction du type de modification ayant eu lieu, puis vous appliquez les modifications à la destination.  
  
#### <a name="to-add-a-data-flow-task-to-the-package"></a>Pour ajouter une tâche de flux de données au package  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], sous l’onglet **Flux de contrôle** , ajoutez une tâche de flux de données.  
  
2.  Connectez la tâche précédente de préparation de la chaîne de requête à la tâche de flux de données.  
  
## <a name="configuring-the-source-component-to-query-for-changes"></a>Configuration du composant source pour rechercher les modifications  
 Le composant source utilise la chaîne de requête qui a été préparée et stockée dans une variable pour appeler la fonction table qui récupère les données modifiées.  
  
> [!NOTE]  
>  Pour plus d’informations sur la chaîne de requête qui a été préparée et stockée dans une variable, consultez [Préparer la recherche des données modifiées](../../integration-services/change-data-capture/prepare-to-query-for-the-change-data.md). Pour plus d’informations sur la fonction table qui récupère les données modifiées, consultez [Créer la fonction de récupération des données modifiées](../../integration-services/change-data-capture/create-the-function-to-retrieve-the-change-data.md).  
  
#### <a name="to-configure-an-ole-db-source-to-retrieve-the-change-data"></a>Pour configurer une source OLE DB pour récupérer les données modifiées  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], sous l’onglet **Flux de données** , ajoutez une source OLE DB.  
  
2.  Dans **l’Éditeur de source OLE DB**, dans la page **Gestionnaire de connexions** , sélectionnez les options suivantes :  
  
    1.  Configurez une connexion valide à la base de données source.  
  
    2.  Pour **Mode d’accès aux données**, sélectionnez **Commande SQL à partir d’une variable**.  
  
    3.  Pour **Nom de variable**, sélectionnez **User::SqlDataQuery**.  
  
3.  Dans **l’Éditeur de source OLE DB**, dans la page **Colonnes** , vérifiez que toutes les colonnes souhaitées sont mappées à des colonnes de sortie.  
  
## <a name="next-step"></a>Étape suivante  
 Après avoir configuré une source OLE DB pour récupérer les données modifiées, l'étape suivante consiste à commencer à concevoir le flux de données dans le package.  
  
 **Rubrique suivante :** [Traiter les insertions, les mises à jour et les suppressions](../../integration-services/change-data-capture/process-inserts-updates-and-deletes.md)  
  
  

