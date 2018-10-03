---
title: Service web, tâche | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicetask.f1
helpviewer_keywords:
- Web Service task [Integration Services]
ms.assetid: 5c7206f1-7d6a-4923-8dff-3c4912da4157
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6a83900ff92611778bb5b71574a7e98ce5e6df18
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48189185"
---
# <a name="web-service-task"></a>Tâche de service Web
  La tâche de service Web exécute une méthode de service Web. Vous pouvez utiliser la tâche de service Web pour :  
  
-   Écrire dans une variable les valeurs renvoyées par une méthode de service Web. Vous pouvez par exemple obtenir la température la plus élevée de la journée à partir d'une méthode de service Web, puis utiliser cette valeur pour mettre à jour une variable utilisée dans une expression qui définit une valeur de colonne.  
  
-   Écrire dans un fichier les valeurs renvoyées par une méthode de service Web. Une liste de clients potentiels peut par exemple être enregistrée dans un fichier qui est ensuite utilisé comme source de données dans un package qui nettoie les données avant de les écrire dans une base de données.  
  
## <a name="wsdl-file"></a>Fichier WSDL  
 La tâche de service Web utilise un gestionnaire de connexions HTTP pour se connecter au service Web. Ce gestionnaire est configuré séparément de la tâche de service Web et est référencé dans la tâche. Le gestionnaire de connexions HTTP spécifie les paramètres proxy du serveur comme l'URL du serveur, les informations d'identification permettant d'accéder au serveur de services Web et la durée du délai d'attente. Pour plus d’informations, consultez [Gestionnaire de connexions HTTP](../connection-manager/http-connection-manager.md).  
  
> [!IMPORTANT]  
>  Le gestionnaire de connexions HTTP prend en charge uniquement l'authentification anonyme et l'authentification de base. Il ne prend pas en charge l'authentification Windows.  
  
 Le gestionnaire de connexions HTTP peut pointer vers un site Web ou un fichier WSDL (Web Service Description Language). L'URL du gestionnaire de connexions HTTP qui pointe vers un fichier WSDL contient le paramètre `?WSDL` , par exemple `http://MyServer/MyWebService/MyPage.asmx?WSDL`.  
  
 Le fichier WSDL doit être disponible localement pour pouvoir configurer la tâche de service web à l’aide de la boîte de dialogue **Éditeur de tâche de service Web** du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] .  
  
-   Si le gestionnaire de connexions HTTP pointe vers un site Web, le fichier WSDL doit être copié manuellement sur un ordinateur local.  
  
-   Si le gestionnaire de connexions HTTP pointe vers un fichier WSDL, ce fichier peut être téléchargé à partir du site Web vers un fichier local par la tâche de service Web.  
  
 Le fichier WSDL énumère les méthodes offertes par le service Web, les paramètres d'entrée requis par les méthodes, les réponses renvoyées par les méthodes et la manière de communiquer avec le service Web.  
  
 Si la méthode utilise des paramètres d'entrée, la tâche de service Web requiert des valeurs de paramètres. Par exemple, une méthode de service Web qui recommande la longueur des skis que vous devez acheter en fonction de votre taille exige que votre taille soit soumise dans un paramètre d'entrée. Les valeurs de paramètres peuvent être fournies par des chaînes définies dans la tâche ou par des variables définies dans l'étendue de la tâche ou un conteneur parent. L'avantage d'utiliser des variables est de vous permettre de mettre à jour dynamiquement les valeurs de paramètres en utilisant des scripts ou des configurations de package. Pour plus d’informations, consultez [Variables Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md) et [Configurations de package](../package-configurations.md).  
  
 De nombreuses méthodes de service Web n'utilisent pas de paramètres d'entrée. Par exemple, une méthode de service Web qui obtient le nom des présidents dont le mois de naissance correspond au mois en cours ne requiert pas de paramètre d'entrée car le service Web peut déterminer le mois en cours localement.  
  
 Les résultats de la méthode de service Web peuvent être écrits dans une variable ou dans un fichier. Vous pouvez utiliser le gestionnaire de connexions de fichiers pour spécifier le fichier ou indiquer le nom de la variable dans laquelle écrire les résultats. Pour plus d’informations, consultez [Gestionnaire de connexions de fichiers](../connection-manager/file-connection-manager.md) et [Variables Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md).  
  
## <a name="custom-logging-messages-available-on-the-web-service-task"></a>Messages de journalisation personnalisés disponibles dans la tâche de service Web  
 Le tableau suivant répertorie les entrées de journal personnalisées de la tâche de service Web. Pour plus d’informations, consultez [Journalisation d’Integration Services &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md) et [Messages personnalisés pour la journalisation](../custom-messages-for-logging.md).  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`WSTaskBegin`|La tâche a commencé à accéder à un service Web.|  
|`WSTaskEnd`|La tâche a terminé une méthode de service Web.|  
|`WSTaskInfo`|Donne des informations détaillées relatives à la tâche.|  
  
## <a name="configuration-of-the-web-service-task"></a>Configuration de la tâche de service Web  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d'informations sur les propriétés définissables dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur l'une des rubriques suivantes :  
  
-   [Éditeur de tâche de service Web &#40;page Général&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Éditeur de tâche de service Web &#40;page Entrée&#41;](../web-service-task-editor-input-page.md)  
  
-   [Éditeur de tâche de service Web &#40;page Sortie&#41;](../web-service-task-editor-output-page.md)  
  
-   [Page Expressions](../expressions/expressions-page.md)  
  
 Pour plus d'informations sur la définition de ces propriétés dans le concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , cliquez sur la rubrique suivante :  
  
-   [Définir les propriétés d’une tâche ou d’un conteneur](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-web-service-task"></a>Configuration par programmation de la tâche de service web  
 Pour plus d'informations sur la définition par programmation de ces propriétés, cliquez sur l'une des rubriques suivantes :  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.WebServiceTask.WebServiceTask>  
  
## <a name="related-content"></a>Contenu associé  
 Vidéo, [Procédure : appeler un service Web à l’aide de la tâche Service Web (vidéo liée à SQL Server)](http://go.microsoft.com/fwlink/?LinkId=259642), sur technet.microsoft.com.  
  
 Réponse traitée, [Consume Web Services in SSIS using Scripts](http://go.microsoft.com/fwlink/?LinkId=321996)(Consommer des services web dans SSIS à l’aide de scripts), sur curatedviews.cloudapp.net.  
  
  
