---
title: Utilisation de gestionnaires de connexions par programmation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- connection managers [Integration Services], programming
ms.assetid: 2686fe84-1ecc-48b8-9160-e7122274bd84
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 973cb7dcfe7eb95e003428adf0c8a0beb7e68e87
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62877700"
---
# <a name="working-with-connection-managers-programmatically"></a>Utilisation de gestionnaires de connexions par programme
  Dans [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], la méthode AcquireConnection de la classe de gestionnaire de connexions associée est celle que vous appelez le plus souvent quand vous utilisez des gestionnaires de connexions dans le code managé. Quand vous écrivez du code managé, vous devez appeler la méthode AcquireConnection pour utiliser les fonctionnalités d’un gestionnaire de connexions. Vous devez appeler cette méthode que vous écriviez du code managé dans une tâche de script, un composant Script, un objet personnalisé ou une application personnalisée.  
  
 Pour appeler correctement la méthode AcquireConnection, vous devez pouvoir répondre aux questions suivantes :  
  
-   **Quels gestionnaires de connexions retournent un objet managé à partir de la méthode AcquireConnection ?**  
  
     De nombreux gestionnaires de connexions retournent des objets COM non managés (System.__ComObject) qui ne peuvent pas être facilement utilisés à partir du code managé. La liste de ces gestionnaires de connexions inclut le gestionnaire de connexions OLE DB fréquemment utilisé.  
  
-   **Pour les gestionnaires de connexions qui retournent un objet managé, quels sont les objets retournés par leurs méthodes AcquireConnection ?**  
  
     Pour caster la valeur de retour en type approprié, vous devez connaître le type d’objet retourné par la méthode AcquireConnection. Par exemple, la méthode AcquireConnection du gestionnaire de connexions [!INCLUDE[vstecado](../includes/vstecado-md.md)] retourne un objet SqlConnection ouvert quand vous utilisez le fournisseur SqlClient. Toutefois, la méthode AcquireConnection du gestionnaire de connexions de fichiers ne retourne qu’une chaîne.  
  
 Cette rubrique répond à ces questions pour les gestionnaires de connexions inclus dans [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].  
  
## <a name="connection-managers-that-do-not-return-a-managed-object"></a>Gestionnaires de connexions qui ne retournent pas un objet managé  
 Le tableau suivant répertorie les gestionnaires de connexions qui retournent un objet COM natif (System.__ComObject) à partir de la méthode AcquireConnection. Ces objets non managés ne peuvent pas être facilement utilisés à partir du code managé.  
  
|Type du gestionnaire de connexions|Nom du gestionnaire de connexions|  
|-----------------------------|-----------------------------|  
|ADO|Gestionnaire de connexions ADO|  
|MSOLAP90|Gestionnaire de connexions [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]|  
|EXCEL|Gestionnaire de connexions Excel|  
|FTP|Gestionnaires de connexion FTP|  
|HTTP|Gestionnaire de connexions HTTP|  
|ODBC|Gestionnaire de connexions ODBC|  
|OLEDB|Gestionnaire de connexions OLE DB|  
  
 En général, vous pouvez utiliser un gestionnaire de connexions [!INCLUDE[vstecado](../includes/vstecado-md.md)] à partir de code managé pour vous connecter à une source de données ADO, Excel, ODBC ou OLE DB.  
  
## <a name="return-values-from-the-acquireconnection-method"></a>Valeurs de retour de la méthode AcquireConnection  
 Le tableau suivant répertorie les gestionnaires de connexions qui retournent un objet managé à partir de la méthode AcquireConnection. Ces objets managés peuvent être facilement utilisés à partir du code managé.  
  
|Type du gestionnaire de connexions|Nom du gestionnaire de connexions|Type de valeur de retour|Informations supplémentaires|  
|-----------------------------|-----------------------------|--------------------------|----------------------------|  
|[!INCLUDE[vstecado](../includes/vstecado-md.md)]|Gestionnaire de connexions [!INCLUDE[vstecado](../includes/vstecado-md.md)]|`System.Data.SqlClient.SqlConnection`||  
|FILE|Gestionnaire de connexions de fichiers|`System.String`|Chemin d'accès au fichier.|  
|FLATFILE|Gestionnaire de connexions de fichiers plats|`System.String`|Chemin d'accès au fichier.|  
|MSMQ|Gestionnaire de connexions MSMQ|`System.Messaging.MessageQueue`||  
|MULTIFILE|Gestionnaire de connexions de fichiers multiples|`System.String`|Chemin d'accès à l'un des fichiers.|  
|MULTIFLATFILE|Gestionnaire de connexions de fichiers plats multiples|`System.String`|Chemin d'accès à l'un des fichiers.|  
|SMOServer|Gestionnaire de connexions SMO|`Microsoft.SqlServer.Management.Smo.Server`||  
|SMTP|Gestionnaire de connexions SMTP|`System.String`|Par exemple : `SmtpServer=<server name>;UseWindowsAuthentication=True;EnableSsl=False;`|  
|WMI|Gestionnaire de connexions WMI|`System.Management.ManagementScope`||  
|SQLMOBILE|Gestionnaire de connexions SQL Server Compact|`System.Data.SqlServerCe.SqlCeConnection`||  
  
![Icône Integration Services (petite)](media/dts-16.gif "icône Integration Services (petite)")**rester jusqu'à la Date avec Integration Services**<br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion à des sources de données dans la tâche de script](extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)   
 [Connexion aux sources de données dans le composant Script](extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)   
 [Connexion à des sources de données dans une tâche personnalisée](extending-packages-custom-objects/task/connecting-to-data-sources-in-a-custom-task.md)  
  
  
