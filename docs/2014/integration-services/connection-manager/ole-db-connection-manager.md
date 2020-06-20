---
title: Gestionnaire de connexions OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- OLE DB connection manager
- data sources [Integration Services], connections
- connection managers [Integration Services], OLE DB
- connections [Integration Services], OLE DB
ms.assetid: 91e3622e-4b1a-439a-80c7-a00b90d66979
author: janinezhang
ms.author: janinez
ms.openlocfilehash: b075bb2830ab911e92ecd7efbd76e7b089e89629
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84920501"
---
# <a name="ole-db-connection-manager"></a>Gestionnaire de connexions OLE DB
  Un gestionnaire de connexions OLE DB permet à un package de se connecter à une source de données à l'aide d'un fournisseur OLE DB. Par exemple, un gestionnaire de connexions OLE DB qui se connecte à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut utiliser le fournisseur [!INCLUDE[msCoName](../../includes/msconame-md.md)] OLE DB pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!NOTE]
>  Le fournisseur OLEDB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 11.0 ne prend pas en charge les mots clés de la nouvelle chaîne de connexion (MultiSubnetFailover=True) pour le clustering de basculement de sous-réseaux multiples. Pour plus d’informations, consultez les [notes de publication de SQL Server](https://go.microsoft.com/fwlink/?LinkId=247824) et le billet de blog [AlwaysOn multi-Subnet Failover and SSIS](https://www.mattmasson.com/2012/03/alwayson-multi-subnet-failover-and-ssis/), sur www.mattmasson.com.  
  
 Plusieurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] tâches et composants de processus de données utilisent un gestionnaire de connexions OLE DB. Ainsi, la source et la destination OLE DB utilisent ce gestionnaire de connexions pour extraire et charger des données, tandis que la tâche d’exécution SQL utilise ce gestionnaire pour se connecter à une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] afin d’exécuter des requêtes.  
  
 Le gestionnaire de connexions OLE DB est également utilisé pour accéder à des sources de données OLE DB dans des tâches personnalisées écrites dans du code non géré utilisant un langage comme C++.  
  
 Lorsque vous ajoutez un gestionnaire de connexions OLE DB à un package, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée un gestionnaire de connexions qui sera converti en connexion OLE DB au moment de l'exécution, définit les propriétés du gestionnaire de connexions et ajoute le gestionnaire de connexions à la collection `Connections` du package.  
  
 La propriété `ConnectionManagerType` du gestionnaire de connexions a pour valeur `OLEDB`.  
  
 Le gestionnaire de connexions OLE DB peut être configuré de plusieurs manières :  
  
-   Indiquez une chaîne de connexion spécifique configurée pour répondre aux besoins du fournisseur sélectionné.  
  
-   Selon le fournisseur, incluez le nom de la source de données à laquelle se connecter.  
  
-   Fournissez les informations d'identification de sécurité nécessaires selon le fournisseur sélectionné.  
  
-   Indiquez si la connexion créée à partir du gestionnaire de connexions est conservée au moment de l'exécution.  
  
## <a name="logging"></a>Journalisation  
 Vous pouvez consigner les appels que le gestionnaire de connexions OLE DB effectue vers des fournisseurs de données externes. Cette fonctionnalité de journalisation permet de résoudre des problèmes liés aux connexions que le gestionnaire de connexions OLE DB établit avec des sources de données externes. Pour consigner les appels que le gestionnaire de connexions OLE DB effectue auprès des fournisseurs de données externes, activez la journalisation des packages et sélectionnez l’événement **diagnostic** au niveau du package. Pour plus d’informations, consultez [Outils de dépannage pour l’exécution des packages](../troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
## <a name="configuration-of-the-oledb-connection-manager"></a>Configuration du gestionnaire de connexions OLEDB  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation. Pour plus d’informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez [Configurer le gestionnaire de connexions OLE DB](../configure-ole-db-connection-manager.md). Pour plus d’informations sur la configuration d’un gestionnaire de connexions par programmation, consultez la documentation de la classe **T:Microsoft.SqlServer.Dts.Runtime.ConnectionManager** dans le Guide du développeur.  
  
## <a name="related-content"></a>Contenu associé  
  
-   Article wiki, [SSIS avec connecteurs Oracle](https://go.microsoft.com/fwlink/?LinkId=220670) sur social.technet.Microsoft.com.  
  
-   Article technique, [Connection Strings for OLE DB Providers](https://go.microsoft.com/fwlink/?LinkId=220744)(Chaînes de connexion pour les fournisseurs OLE DB), sur carlprothman.net.  
  
## <a name="see-also"></a>Voir aussi  
 [Source de OLE DB](../data-flow/ole-db-source.md)   
 [Destination de la OLE DB](../data-flow/ole-db-destination.md)   
 [Tâche d’exécution SQL](../control-flow/execute-sql-task.md)   
 [Connexions Integration Services &#40;SSIS&#41;](integration-services-ssis-connections.md)  
  
  
