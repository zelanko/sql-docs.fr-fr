---
title: Générer de fichiers de vidage pour l’exécution des packages | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 61ef1731-cb3a-4afb-b4a4-059b04aeade0
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8022532dcb038b7c9a5839acb0541337ac3d5001
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62766146"
---
# <a name="generating-dump-files-for-package-execution"></a>Générer de fichiers de vidage pour l'exécution des packages
  Dans [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], vous pouvez créer des fichiers de vidage du débogage qui fournissent des informations sur l’exécution d’un package. Les informations contenues dans ces fichiers peuvent vous aider à résoudre des problèmes d'exécution du package.  
  
> [!NOTE]  
>  Les fichiers de vidage de débogage peuvent contenir des informations sensibles. Pour protéger les informations sensibles, vous pouvez utiliser une liste de contrôle d'accès (ACL) afin de restreindre l'accès aux fichiers ou copier les fichiers dans un dossier avec accès limité. Par exemple, nous vous recommandons de supprimer toutes les informations sensibles ou confidentielles avant d'envoyer vos fichiers de débogage aux services de support technique de [!INCLUDE[msCoName](../../includes/msconame-md.md)] .  
  
 Lorsque vous déployez un projet sur le serveur [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] , vous pouvez créer des fichiers de vidage qui fournissent des informations sur l'exécution des packages contenus dans le projet. Lorsque le processus ISServerExec.exe se termine, les fichiers de vidage sont créés. Vous pouvez spécifier qu'un fichier de vidage doit être créé lorsque des erreurs se produisent durant l'exécution du package. Pour ce faire, sélectionnez l'option **Vider en cas d'erreurs** dans la boîte de dialogue **Exécuter le package** . Vous pouvez également utiliser les procédures stockées suivantes :  
  
-   [catalog.set_execution_parameter_value &#40;base de données SSISDB&#41;](/sql/integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database)  
  
     Appelez cette procédure stockée pour configurer un fichier de vidage à créer lorsqu'une erreur ou un événement se produit, et lorsque des événements spécifiques se produisent, au cours de l'exécution d'un package.  
  
-   [catalog.create_execution_dump](/sql/integration-services/system-stored-procedures/catalog-create-execution-dump)  
  
     Appelez cette procédure stockée pour obliger un package à interrompre son exécution et créer un fichier de vidage.  
  
 Si vous déployez des packages à l’aide du modèle de déploiement de package, vous créez les fichiers de vidage du débogage à l’aide de l’utilitaire **dtexec** ou de l’utilitaire **dtutil** pour spécifier une option de vidage du débogage sur la ligne de commande. Pour plus d'informations, consultez [dtexec Utility](../packages/dtexec-utility.md) et [dtutil Utility](../dtutil-utility.md). Pour plus d’informations sur le modèle de déploiement de package, consultez [déploiement de projets et Packages](../packages/deploy-integration-services-ssis-projects-and-packages.md) et [déploiement de Package &#40;SSIS&#41;](../packages/legacy-package-deployment-ssis.md).  
  
## <a name="debug-dump-file-format"></a>Format des fichiers de vidage du débogage  
 Lorsque vous spécifiez une option de vidage de débogage, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] crée les fichiers de vidage de débogage suivants :  
  
-   Un fichier de vidage de débogage .mdmp. Il s'agit d'un fichier binaire.  
  
-   Fichier de vidage de débogage .tmp. Il s'agit d'un fichier au format texte.  
  
 Par défaut, [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] stocke ces fichiers dans le dossier *\<lecteur>:* \Program Files\Microsoft SQL Server\110\Shared\ErrorDumps.  
  
 Le tableau ci-dessous décrit uniquement certaines sections du fichier .tmp. Le fichier .tmp inclut des données supplémentaires qui ne sont pas répertoriées dans ce tableau.  
  
|Type d'informations|Description|Exemple|  
|-------------------------|-----------------|-------------|  
|Environnement|Version de système d'exploitation, données d'utilisation de la mémoire, ID de processus et nom d'image de processus. Les informations d'environnement se trouvent au début du fichier .tmp.|# Vidage texte SSIS effectué le 13/09/2007 à 13:50:34<br /><br /> # PID 4120<br /><br /> #Nom de l'image [C:\Program Files\Microsoft SQL Server\110\DTS\Binn\DTExec.exe]<br /><br /> # OS major=6 minor=0 build=6000<br /><br /> # Exécution sur 2 processeurs amd64 sous WOW64<br /><br /> # Mémoire : 58 % utilisés. Physique : 845M/2044M  Pagination : 2404M/4095M (dispo/total)|  
|Chemin d'accès et version des bibliothèques de liens dynamiques (DLL)|Chemin d'accès et numéro de version de chaque DLL que le système charge pendant le traitement d'un package.|# Module chargé : c:\bb\Sql\DTS\src\bin\debug\i386\DTExec.exe (10.0.1069.5)<br /><br /> # Module chargé : C:\Windows\SysWOW64\ntdll.dll (6.0.6000.16386)<br /><br /> # Module chargé : C:\Windows\syswow64\kernel32.dll (6.0.6000.16386)|  
|Messages récents|Messages récents émis par le système. Inclut l'heure, le type, la description et l'ID de thread de chaque message.|[M:1]   Ring buffer entry:              (*pRecord)<br /><br /> [D:2]      <<\<CRingBufferLogging::RingBufferLoggingRecord>>> ( \@ 0282F1A8 )<br /><br /> [E:3]         Horodatage : 2007-09-13 13:50:32.786      (szTimeStamp)<br /><br /> [E:3]         ID du thread : 2368           (ThreadID)<br /><br /> [E:3]         Nom d'événement : OnError                        (EventName)<br /><br /> [E:3]         Nom de la source :                (SourceName)<br /><br /> [E:3]         ID de la source :                        (SourceID)<br /><br /> [E:3]         ID d'exécution :                 (ExecutionGUID)<br /><br /> [E:3]         Data Code: -1073446879              (DataCode)<br /><br /> [E:3]         Description : Le composant est manquant, n'est pas enregistré, ne peut pas être mis à niveau ou des interfaces obligatoires sont manquantes. Informations de contact de ce composant : «  ».|  
  
## <a name="related-content"></a>Contenu associé  
 [Exécuter le package, boîte de dialogue](../execute-package-dialog-box.md)  
  
  
