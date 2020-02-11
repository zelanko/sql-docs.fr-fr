---
title: Outils de dépannage connectivité des packages | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services packages, troubleshooting
- SSIS packages, troubleshooting
- Integration Services, troubleshooting
- connectivity [Integration Services], troubleshooting
- errors [Integration Services], troubleshooting
- packages [Integration Services], troubleshooting
ms.assetid: 08a019f5-8ba7-4527-97c1-e9846d4022ff
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8bb86d738aed61743defa3261318e2eb7536aa84
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62766162"
---
# <a name="troubleshooting-tools-package-connectivity"></a>Outils de dépannage de la connectivité des packages
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] inclut des fonctionnalités et des outils que vous pouvez utiliser pour dépanner la connectivité entre les packages et les sources de données à partir desquelles les packages extraient et chargent des données.  
  
## <a name="troubleshooting-issues-with-external-data-providers"></a>Dépannage des problèmes liés aux fournisseurs de données externes  
 Beaucoup de packages échouent lorsqu'ils communiquent avec des fournisseurs de données externes. Néanmoins, les messages que retournent ces fournisseurs à [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] apportent souvent des informations insuffisantes pour commencer à résoudre cet échec de communication. Pour traiter ce problème, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] inclut des messages de journalisation qui vous permettent de résoudre les problèmes d'interaction d'un package avec des sources de données externes.  
  
-   **Activez la journalisation et sélectionnez l’événement Diagnostic du package pour afficher les messages de dépannage**. Les composants [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] suivants peuvent écrire un message dans le journal avant et après chaque appel à un fournisseur de données externes :  
  
    -   Gestionnaire de connexions OLE DB, source OLE DB et destination OLE DB  
  
    -   Gestionnaire de connexions [!INCLUDE[vstecado](../../includes/vstecado-md.md)] et source ADO NET  
  
    -   Tâche d'exécution de requêtes SQL  
  
    -   Transformation de recherche, transformation de commande OLE DB et transformation de dimension à variation lente  
  
     Les messages de journal contiennent le nom de la méthode appelée. Par exemple, ils peuvent inclure la méthode `Open` d'un objet OLE DB `Connection` ou la méthode `ExecuteNonQuery` d'un objet `Command`. Les messages ont le format suivant, où '%1!s!' est un emplacement réservé pour les informations de méthode :  
  
    ```  
    ExternalRequest_pre: The object is ready to make the following external request: '%1!s!'.  
    ExternalRequest_post: '%1!s!'. The external request has completed.  
    ```  
  
     Pour résoudre les problèmes d’interaction avec le fournisseur de données externes, passez en revue le journal pour savoir si chaque message transmis « avant » (`ExternalRequest_pre` dispose d’un message transmis « après » (`ExternalRequest_post`) correspondant. Si aucun message postérieur correspondant n'existe, vous savez alors que le fournisseur de données externes n'a pas répondu comme prévu.  
  
     L'exemple suivant présente quelques exemples de lignes d'un journal contenant ces messages de journalisation :  
  
    ```  
    ExternalRequest_pre: The object is ready to make the following external request: 'ITransactionJoin::JoinTransaction'.  
    ExternalRequest_post: 'ITransactionJoin::JoinTransaction succeeded'. The external request has completed.  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.Open'.  
    ExternalRequest_post: 'IDbConnection.Open succeeded'. The external request has completed.  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.CreateCommand'.  
    ExternalRequest_post: 'IDbConnection.CreateCommand finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbCommand.ExecuteReader'.  
    ExternalRequest_post: 'IDbCommand.ExecuteReader finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDataReader.GetSchemaTable'.  
    ExternalRequest_post: 'IDataReader.GetSchemaTable finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDataReader.Close'.  
    ExternalRequest_post: 'IDataReader.Close finished'. The external request has completed."  
    ExternalRequest_pre: The object is ready to make the following external request: 'IDbConnection.Close'.  
    ExternalRequest_post: 'IDbConnection.Close finished'. The external request has completed."  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de dépannage pour le développement des packages](troubleshooting-tools-for-package-development.md)   
 [Outils de dépannage pour l’exécution des packages](troubleshooting-tools-for-package-execution.md)  
  
  
