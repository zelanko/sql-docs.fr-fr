---
title: Éditeur de tâche de profilage de données (page Général) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataprofilingtask.general.f1
helpviewer_keywords:
- Data Profiling Task Editor
ms.assetid: eec15906-d757-4079-b2f6-aca4e52b3b4c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8462f85dc6c804020f12b9bc989d683c5a4ad0ba
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62832215"
---
# <a name="data-profiling-task-editor-general-page"></a>Éditeur de tâche de profilage de données (page Général)
  Utilisez la page **Général** de l' **Éditeur de tâche de profilage de données** pour configurer les options suivantes :  
  
-   Spécifiez la destination de la sortie du profil.  
  
-   Utilisez les paramètres par défaut pour simplifier la tâche de profilage d'une table ou vue unique.  
  
 Pour plus d’informations sur l’utilisation de la tâche de profilage des données, consultez [Configuration de la tâche de profilage des données](data-profiling-task.md). Pour plus d’informations sur l’utilisation de la visionneuse du profil des données pour analyser le résultat de la tâche de profilage des données, consultez [Visionneuse du profil des données](data-profile-viewer.md).  
  
 **Pour ouvrir la page Général de l'Éditeur de tâche de profilage de données**  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] doté de la tâche de profilage de données.  
  
2.  Sous l’onglet **Flux de contrôle** , double-cliquez sur la tâche de profilage des données.  
  
3.  Dans l' **Éditeur de tâche de profilage de données**, cliquez sur **Général**.  
  
## <a name="data-profiling-options"></a>Options de profilage des données  
 **Délai d'expiration**  
 Spécifiez le nombre de secondes après lesquelles la tâche de profilage des données doit expirer et ne plus s'exécuter. La valeur par défaut est 0, ce qui indique l'absence de délai d'expiration.  
  
## <a name="destination-options"></a>Options de destination  
  
> [!IMPORTANT]  
>  Le fichier de sortie peut contenir des données sensibles qui concernent votre base de données et les données qu'elle contient. Pour obtenir des suggestions sur la manière de sécuriser davantage ce fichier, consultez [Accéder aux fichiers utilisés par des packages](../access-to-files-used-by-packages.md).  
  
 **DestinationType**  
 Spécifiez si la sortie du profil des données doit être enregistrée dans un fichier ou une variable :  
  
|Value|Description|  
|-----------|-----------------|  
|**FileConnection**|Enregistrez la sortie du profil dans un fichier à l'emplacement spécifié dans un gestionnaire de connexions de fichiers.<br /><br /> Remarque : Vous devez spécifier le gestionnaire de connexions de fichiers à utiliser dans l'option **Destination**.|  
|**Variable**|Enregistrez la sortie du profil dans une variable de package.<br /><br /> Remarque : Vous devez spécifier la variable de package à utiliser dans l'option **Destination**.|  
  
 **Destination**  
 Spécifiez le gestionnaire de connexions de fichiers ou la variable de package qui contient la sortie du profil des données :  
  
-   Si l'option **DestinationType** est définie sur **FileConnection**, l'option **Destination** affiche les gestionnaires de connexions de fichiers disponibles. Choisissez l’un de ces gestionnaires de connexions ou sélectionnez \<Nouvelle connexion de fichier> pour créer un nouveau gestionnaire de connexions de fichiers.  
  
-   Si l'option **DestinationType** est définie sur **Variable**, l'option **Destination** affiche les variables de package disponibles dans la liste **Destination** . Choisissez l’une de ces variables ou sélectionnez \<Nouvelle variable> pour créer une variable.  
  
 **OverwriteDestination**  
 Spécifiez si le fichier de sortie est à remplacer s'il existe déjà. La valeur par défaut est **False**. La valeur de cette propriété est utilisée uniquement lorsque l'option DestinationType est définie sur FileConnection. Lorsque l'option DestinationType est définie sur Variable, la tâche remplace toujours la valeur précédente de la variable.  
  
> [!IMPORTANT]  
>  Si vous tentez d’exécuter la tâche de profilage des données plus d’une fois sans modifier le nom du fichier de sortie ou redéfinir la valeur de la propriété **OverwriteDestination** sur **True**, la tâche échoue et affiche un message indiquant que le fichier de sortie existe déjà.  
  
## <a name="other-options"></a>Autres options  
 **Profil rapide**  
 Affichez le **Formulaire de profil rapide de table simple**. Ce formulaire simplifie la tâche de profilage d'une table ou d'une vue unique à l'aide des paramètres par défaut. Pour plus d’informations, consultez [Formulaire de profil rapide de table simple &#40;tâche de profilage des données&#41;](single-table-quick-profile-form-data-profiling-task.md).  
  
 **Ouvrir la visionneuse de profil**  
 Ouvre la visionneuse du profil des données. La visionneuse de profil des données autonome affiche la sortie du profil des données de la tâche de profilage des données. Pour afficher la sortie du profil des données, vous devez avoir exécuté la tâche de profilage des données dans le package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et avoir calculé les profils des données.  
  
> [!NOTE]  
>  Pour ouvrir la Visionneuse du profil des données, vous pouvez aussi exécuter DataProfileViewer.exe dans le dossier, *\<lecteur>* :\Program Files (x86) | Program Files\Microsoft SQL Server\110\DTS\Binn.  
  
## <a name="see-also"></a>Voir aussi  
 [Formulaire de profil rapide de table simple &#40;tâche de profilage des données&#41;](single-table-quick-profile-form-data-profiling-task.md)   
 [Éditeur de tâche de profilage de données &#40;page Demandes de profil&#41;](data-profiling-task-editor-profile-requests-page.md)  
  
  
