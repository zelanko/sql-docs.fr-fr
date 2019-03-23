---
title: XML, tâche | Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ftptask.f1
helpviewer_keywords:
- FTP task [Integration Services]
ms.assetid: 41c3f2c4-ee04-460a-9822-bb9ae4036c2e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: fcc071c10a2daa31190727dfc9f3cbe617bdcb66
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58382197"
---
# <a name="ftp-task"></a>Tâche FTP
  La tâche FTP télécharge des fichiers de données et gère des répertoires sur les serveurs. Par exemple, un package peut télécharger des fichiers de données à partir d’un serveur distant ou d’un emplacement Internet dans le cadre d’un flux de travail de package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] . Vous pouvez utiliser la tâche FTP aux fins suivantes :  
  
-   Copie de répertoires et de fichiers de données depuis un répertoire vers un autre, avant ou après le déplacement de données, et application de transformations aux données  
  
-   Connexion à un emplacement FTP source et copie des fichiers ou des packages vers un répertoire de destination  
  
-   Téléchargement de fichiers depuis un emplacement FTP et application de transformations aux données de colonne avant de charger les données dans une base de données  
  
 À l'exécution, la tâche FTP se connecte à un serveur à l'aide d'un gestionnaire de connexions FTP. Le gestionnaire de connexions FTP est configuré indépendamment de la tâche FTP, puis il est référencé dans celle-ci. Le gestionnaire de connexions FTP comprend les paramètres de serveur, les informations d'identification d'accès au serveur FTP et des options telles que le délai d'attente et le nombre de tentatives de connexion au serveur. Pour plus d’informations, consultez [Gestionnaires de connexion FTP](../connection-manager/ftp-connection-manager.md).  
  
> [!IMPORTANT]  
>  Le gestionnaire de connexions FTP prend en charge uniquement l'authentification anonyme et l'authentification de base. Il ne prend pas en charge l'authentification Windows.  
  
 Pour accéder à un fichier local ou à un répertoire local, la tâche FTP utilise un gestionnaire de connexions de fichiers ou des informations de chemin d'accès stockées dans une variable. À l'inverse, pour accéder à un fichier distant ou à un répertoire distant, la tâche FTP utilise un chemin d'accès directement spécifié sur le serveur distant, tel qu'indiqué dans le gestionnaire de connexions FTP, ou des informations de chemin d'accès stockées dans une variable. Pour plus d’informations, consultez [Gestionnaire de connexions de fichiers](../connection-manager/file-connection-manager.md) et [Variables Integration Services &#40;SSIS&#41;](../integration-services-ssis-variables.md).  
  
 Cela signifie que la tâche FTP peut recevoir plusieurs fichiers et supprimer plusieurs fichiers distants ; toutefois, la tâche peut envoyer seulement un fichier et supprimer seulement un fichier local si elle utilise un gestionnaire de connexions, car un gestionnaire de connexions de fichiers ne peut accéder qu'à un fichier. Pour accéder à plusieurs fichiers locaux, la tâche FTP doit utiliser une variable afin d'indiquer les informations de chemin d'accès. Par exemple, une variable contenant le texte « C:\Test\\*.txt » désigne un chemin qui prend en charge la suppression ou l’envoi de tous les fichiers ayant pour extension .txt et figurant dans le répertoire Test.  
  
 Pour envoyer plusieurs fichiers et accéder à plusieurs fichiers et répertoires locaux, vous pouvez également exécuter la tâche FTP plusieurs fois en l'incluant dans une boucle Foreach. La boucle Foreach peut passer en revue tous les fichiers d'un répertoire à l'aide de l'énumérateur For Each File. Pour plus d’informations, consultez [Conteneur de boucles Foreach](foreach-loop-container.md).  
  
 La tâche FTP prend en charge les caractères génériques *?* et *\** dans les chemins. Cela lui permet d'accéder à plusieurs fichiers. Toutefois, vous pouvez utiliser des caractères génériques seulement dans la partie du chemin d'accès qui spécifie le nom de fichier. Par exemple, « C:\MyDirectory\\*.txt » est un chemin valide, contrairement à « C:\\\**\MyText.txt ».  
  
 Vous pouvez configurer les opérations FTP de manière à ce que la tâche de système de fichiers soit arrêtée en cas d'échec des opérations ou de manière à transférer les fichiers en mode ASCII. De même, vous pouvez configurer les opérations qui envoient et reçoivent des fichiers de manière à ce que les fichiers et les répertoires de destination soient écrasés.  
  
## <a name="predefined-ftp-operations"></a>Opérations FTP prédéfinies  
 La tâche FTP comprend un ensemble prédéfini d'opérations. Le tableau suivant décrit ces opérations.  
  
|Opération|Description|  
|---------------|-----------------|  
|Envoyer des fichiers|Envoie un fichier depuis l'ordinateur local vers le serveur FTP.|  
|Recevoir des fichiers|Enregistre sur l'ordinateur local un fichier provenant du serveur FTP.|  
|Créer un répertoire local|Crée un dossier sur l'ordinateur local.|  
|Créer un répertoire distant|Crée un dossier sur le serveur FTP.|  
|Supprimer le répertoire local|Supprime un dossier de l'ordinateur local.|  
|Supprimer le répertoire distant|Supprime un dossier du serveur FTP.|  
|Supprimer des fichiers locaux|Supprime un fichier de l'ordinateur local.|  
|Supprimer des fichiers distants|Supprime un fichier du serveur FTP.|  
  
## <a name="custom-log-entries-available-on-the-ftp-task"></a>Entrées de journal personnalisées disponibles dans la tâche FTP  
 Le tableau suivant répertorie les entrées de journal personnalisées pour la tâche FTP. Pour plus d’informations, consultez [Journalisation d’Integration Services &#40;SSIS&#41;](../performance/integration-services-ssis-logging.md) et [Messages personnalisés pour la journalisation](../custom-messages-for-logging.md).  
  
|Entrée du journal|Description|  
|---------------|-----------------|  
|`FTPConnectingToServer`|Indique que la tâche a lancé une connexion au serveur FTP.|  
|`FTPOperation`|Indique le démarrage et le type d'une opération FTP effectuée par la tâche.|  
  
## <a name="related-tasks"></a>Tâches associées  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] ou par programmation.  
  
 Pour plus d’informations sur la façon de définir ces propriétés dans le Concepteur [!INCLUDE[ssIS](../../includes/ssis-md.md)] , consultez [Définir les propriétés d’une tâche ou d’un conteneur](../set-the-properties-of-a-task-or-container.md).  
  
 Pour plus d’informations sur la définition de ces propriétés par programmation, consultez <xref:Microsoft.SqlServer.Dts.Tasks.FtpTask.FtpTask>.  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de tâche FTP &#40;page Général&#41;](../general-page-of-integration-services-designers-options.md)   
 [Éditeur de tâche FTP &#40;page Transfert de fichiers&#41;](../ftp-task-editor-file-transfer-page.md)   
 [Tâches Integration Services](integration-services-tasks.md)   
 [Flux de contrôle](control-flow.md)  
  
  
