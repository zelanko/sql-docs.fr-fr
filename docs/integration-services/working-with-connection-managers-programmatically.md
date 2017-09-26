---
title: Utilisation de gestionnaires de connexions par programme | Documents Microsoft
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- connection managers [Integration Services], programming
ms.assetid: 2686fe84-1ecc-48b8-9160-e7122274bd84
caps.latest.revision: 15
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9093b9eadce231aea248cd04c2b57dc5dd5e1a76
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="working-with-connection-managers-programmatically"></a>Utilisation de gestionnaires de connexions par programme
  Dans [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], la méthode AcquireConnection de la classe de gestionnaire de connexion associée est la méthode que vous appelez le plus souvent lorsque vous travaillez avec des gestionnaires de connexions dans le code managé. Lorsque vous écrivez du code managé, vous devez appeler la méthode AcquireConnection pour utiliser la fonctionnalité d’une connexion de gestionnaire. Vous devez appeler cette méthode que vous écriviez du code managé dans une tâche de script, un composant Script, un objet personnalisé ou une application personnalisée.  
  
 Pour appeler la méthode AcquireConnection correctement, vous devez connaître les réponses aux questions suivantes :  
  
-   **Quels gestionnaires de connexions retournent un objet managé à partir de la méthode AcquireConnection ?**  
  
     Plusieurs gestionnaires de connexions retournent des objets COM non managés (System.__ComObject) et ces objets ne peut pas être utilisés facilement à partir du code managé. La liste de ces gestionnaires de connexions inclut le gestionnaire de connexions OLE DB fréquemment utilisé.  
  
-   **Pour les gestionnaires de connexions qui retournent un objet managé, les objets leurs méthodes AcquireConnection retournent ?**  
  
     Pour effectuer un cast de la valeur de retour vers le type approprié, vous devez connaître le type d’objet retourne de la méthode AcquireConnection. Par exemple, la méthode AcquireConnection pour le [!INCLUDE[vstecado](../includes/vstecado-md.md)] Gestionnaire de connexions retourne un objet SqlConnection ouvert lorsque vous utilisez le fournisseur SqlClient. Toutefois, la méthode AcquireConnection pour le Gestionnaire de connexions de fichier retourne simplement une chaîne.  
  
 Cette rubrique répond à ces questions pour les gestionnaires de connexions inclus dans [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
## <a name="connection-managers-that-do-not-return-a-managed-object"></a>Gestionnaires de connexions qui ne retournent pas un objet managé  
 Le tableau suivant répertorie les gestionnaires de connexions qui retournent un objet COM natif (System.__ComObject) à partir de la méthode AcquireConnection. Ces objets non managés ne peuvent pas être facilement utilisés à partir du code managé.  
  
|Type du gestionnaire de connexions|Nom du Gestionnaire de connexions|  
|-----------------------------|-----------------------------|  
|ADO|Gestionnaire de connexions ADO|  
|MSOLAP90|Gestionnaire de connexions [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]|  
|EXCEL|Gestionnaire de connexions Excel|  
|FTP|Gestionnaires de connexion FTP|  
|HTTP|Gestionnaire de connexions HTTP|  
|ODBC|Gestionnaire de connexions ODBC|  
|OLEDB|Gestionnaire de connexions OLE DB|  
  
 En règle générale, vous pouvez utiliser un [!INCLUDE[vstecado](../includes/vstecado-md.md)] Gestionnaire de connexions à partir de code managé pour se connecter à une source de données ADO, Excel, ODBC ou OLE DB.  
  
## <a name="return-values-from-the-acquireconnection-method"></a>Valeurs de retour de la méthode AcquireConnection  
 Le tableau suivant répertorie les gestionnaires de connexions qui retournent un objet managé à partir de la méthode AcquireConnection. Ces objets managés peuvent être facilement utilisés à partir du code managé.  
  
|Type du gestionnaire de connexions|Nom du Gestionnaire de connexions|Type de valeur de retour|Informations supplémentaires|  
|-----------------------------|-----------------------------|--------------------------|----------------------------|  
|[!INCLUDE[vstecado](../includes/vstecado-md.md)]|Gestionnaire de connexions [!INCLUDE[vstecado](../includes/vstecado-md.md)]|**System.Data.SqlClient.SqlConnection**||  
|FILE|Gestionnaire de connexions de fichiers|**System.String**|Chemin d'accès au fichier.|  
|FLATFILE|Gestionnaire de connexions de fichiers plats|**System.String**|Chemin d'accès au fichier.|  
|MSMQ|Gestionnaire de connexions MSMQ|**System.Messaging.MessageQueue**||  
|MULTIFILE|Gestionnaire de connexions de fichiers multiples|**System.String**|Chemin d'accès à l'un des fichiers.|  
|MULTIFLATFILE|Gestionnaire de connexions de fichiers plats multiples|**System.String**|Chemin d'accès à l'un des fichiers.|  
|SMOServer|Gestionnaire de connexions SMO|**Microsoft.SqlServer.Management.Smo.Server**||  
|SMTP|Gestionnaire de connexions SMTP|**System.String**|Par exemple : `SmtpServer=<server name>;UseWindowsAuthentication=True;EnableSsl=False;`|  
|WMI|Gestionnaire de connexions WMI|**System.Management.ManagementScope**||  
|SQLMOBILE|Gestionnaire de connexions SQL Server Compact|**System.Data.SqlServerCe.SqlCeConnection**||  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion aux Sources de données dans la tâche de Script](../integration-services/extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)   
 [Connexion aux Sources de données dans le composant Script](../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)   
 [Connexion à des sources de données dans une tâche personnalisée](../integration-services/extending-packages-custom-objects/task/connecting-to-data-sources-in-a-custom-task.md)  
  
  
