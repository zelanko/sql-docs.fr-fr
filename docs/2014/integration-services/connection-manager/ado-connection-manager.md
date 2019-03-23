---
title: Gestionnaire de connexions ADO | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connections [Integration Services], ADO
- connection managers [Integration Services], ADO
- ADO connection manager [Integration Services]
ms.assetid: 490418bc-5ef1-41b8-a9c8-de38aa96e0f6
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7fda014196d933ef9d5391ab4db798d821e43610
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58376667"
---
# <a name="ado-connection-manager"></a>Gestionnaire de connexions ADO
  Un gestionnaire de connexions ADO permet à un package de se connecter à des objets ADO (ActiveX Data Objects), comme un recordset. Ce gestionnaire de connexions est généralement utilisé dans les tâches personnalisées écrites dans une version antérieure d’un langage comme Microsoft Visual Basic 6.0 ou dans les tâches personnalisées qui font partie d’une application existante utilisant ADO pour se connecter à une source de données.  
  
 Lorsque vous ajoutez un gestionnaire de connexions ADO à un package, [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée une connexion de gestionnaire qui sera converti en connexion ADO au moment de l’exécution, définit des propriétés du Gestionnaire de la connexion et ajoute le Gestionnaire de connexions à la `Connections` collection sur le package. La propriété `ConnectionManagerType` du gestionnaire de connexions a pour valeur `ADO`.  
  
## <a name="troubleshooting-the-ado-connection-manager"></a>Résolution des problèmes liés au gestionnaire de connexions ADO  
 Lors de la lecture par un gestionnaire de connexions ADO, certains types de données de date [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] génèrent les résultats présentés dans le tableau suivant.  
  
|Type de données SQL Server|Résultat|  
|--------------------------|------------|  
|`time`, `datetimeoffset`|Le package échoue s'il n'utilise pas de commandes SQL paramétrables. Pour utiliser des commandes SQL paramétrables, utilisez la tâche d'exécution SQL dans votre package. Pour plus d’informations, consultez [Tâche d’exécution de requêtes SQL](../control-flow/execute-sql-task.md) et [Paramètres et codes de retour dans la tâche d’exécution SQL](../parameters-and-return-codes-in-the-execute-sql-task.md).|  
|`datetime2`|Le gestionnaire de connexions ADO tronque les millisecondes.|  
  
> [!NOTE]  
>  Pour plus d’informations sur les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et leur mappage aux types de données [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], consultez [Types de données &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) et [Types de données d’Integration Services](../data-flow/integration-services-data-types.md).  
  
## <a name="configuring-the-ado-connection-manager"></a>Configuration du gestionnaire de connexions ADO  
 Vous pouvez configurer un gestionnaire de connexions ADO de plusieurs manières :  
  
-   Indiquez une chaîne de connexion spécifique configurée pour répondre aux besoins du fournisseur sélectionné.  
  
-   Selon le fournisseur, incluez le nom de la source de données à laquelle se connecter.  
  
-   Fournissez les informations d'identification de sécurité nécessaires selon le fournisseur sélectionné.  
  
-   Indiquez si la connexion créée à partir du gestionnaire de connexions est conservée au moment de l'exécution.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Configurer le gestionnaire de connexions OLE DB](ole-db-connection-manager.md)  
  
 Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> et [Ajout de connexions par programme](../building-packages-programmatically/adding-connections-programmatically.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Connexions Integration Services &#40;SSIS&#41;](integration-services-ssis-connections.md)  
  
  
