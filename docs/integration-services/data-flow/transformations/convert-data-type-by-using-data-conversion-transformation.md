---
title: "Convertir le Type de données à l’aide de Transformation de Conversion de données | Documents Microsoft"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- converting data types [Integration Services]
- Data Conversion transformation
- data types [Integration Services], converting
ms.assetid: 4aabbe4f-7666-4672-865a-9627bd25fbfd
caps.latest.revision: 41
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: c3e47e4a5ae297202ba43679fba393421880a7ea
ms.openlocfilehash: 3a6de227fc2fd0e93abfc9e8ac5300dbf0a137ac
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="convert-data-type-by-using-data-conversion-transformation"></a>Convertir le Type de données à l’aide de Transformation de Conversion de données
  Pour pouvoir ajouter et configurer une transformation de conversion de données, le package doit inclure au moins une tâche de flux de données et une source.  
  
### <a name="to-convert-data-to-a-different-data-type"></a>Pour convertir des données en un type différent  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], ouvrez le projet [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] contenant le package souhaité.  
  
2.  Dans l'Explorateur de solutions, double-cliquez sur le package pour l'ouvrir.  
  
3.  Cliquez sur l’onglet **Flux de données** et, dans la **boîte à outils**, faites glisser la transformation de conversion de données sur l’aire de conception.  
  
4.  Connectez la transformation de conversion de données au flux de données en faisant glisser un connecteur à partir de la source ou de la transformation précédente vers la transformation de conversion de données.  
  
5.  Double-cliquez sur la transformation de conversion de données.  
  
6.  Dans la boîte de dialogue **Éditeur de transformation de conversion de données** , dans la table **Colonnes d’entrée disponibles** , cochez la case en regard des colonnes dont vous voulez convertir le type de données.  
  
    > [!NOTE]  
    >  Vous pouvez appliquer plusieurs conversions de données à une colonne d'entrée.  
  
7.  Si vous le souhaitez, modifiez les valeurs par défaut de la colonne **Alias de sortie** .  
  
8.  Dans la liste **Type de données** , sélectionnez le nouveau type de données de la colonne. Le type de données par défaut est celui de la colonne d'entrée.  
  
9. Si vous le souhaitez et selon le type de données sélectionné, mettez à jour les valeurs des colonnes **Longueur**, **Précision**, **Échelle**et **Page de codes** .  
  
10. Pour configurer la sortie d’erreur, cliquez sur **Configurer la sortie d’erreur**. Pour plus d’informations, consultez [Débogage d’un flux de données](../../../integration-services/troubleshooting/debugging-data-flow.md).  
  
11. Cliquez sur **OK**.  
  
12. Pour enregistrer le package mis à jour, cliquez sur **Enregistrer les éléments sélectionnés** dans le menu **Fichier** .  
  
## <a name="see-also"></a>Voir aussi  
 [Transformation de Conversion de données](../../../integration-services/data-flow/transformations/data-conversion-transformation.md)   
 [Transformations Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Chemins d’accès d’Integration Services](../../../integration-services/data-flow/integration-services-paths.md)   
 [Types de données Integration Services](../../../integration-services/data-flow/integration-services-data-types.md)   
 [Tâche de flux de données](../../../integration-services/control-flow/data-flow-task.md)  
  
  

