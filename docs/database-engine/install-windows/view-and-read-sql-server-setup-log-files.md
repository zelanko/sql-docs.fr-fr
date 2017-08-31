---
title: "Afficher et lire les fichiers journaux d’installation de SQL Server | Microsoft Docs"
ms.custom: 
ms.date: 03/09/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- setup-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- viewing logs
- displaying log files
- Setup [SQL Server], logs
- installation log files [SQL Server]
- installing SQL Server, logs
- errors [SQL Server], Setup
- logs [SQL Server], Setup
ms.assetid: 9d77af64-9084-4375-908a-d90f99535062
caps.latest.revision: 54
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 21f0cfd102a6fcc44dfc9151750f1b3c936aa053
ms.openlocfilehash: 3f87dec24a195cabd75fb653fcb5bcaf51e29db9
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="view-and-read-sql-server-setup-log-files"></a>Afficher et lire les fichiers journaux d'installation de SQL Server
  Chaque fois que le programme d’installation est exécuté, des fichiers journaux sont créés dans un nouveau dossier de journal horodaté à l’emplacement %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\. Le format du nom du dossier de journal horodaté est AAAAMMJJ_hhmmss. Lorsque le programme d'installation est exécuté en mode sans assistance, les journaux sont créés à l'emplacement % temp%\sqlsetup*.log. Tous les fichiers du dossier de journal sont archivés dans le fichier Log\*.cab dans leur dossier de journal respectif.  
  
 Une demande d'Installation typique passe par trois phases d'exécution :  
  
1.  Texte de règles globales  
  
2.  Mise à jour du composant  
  
3.  Action demandée par l'utilisateur  
  
 Dans chaque phase, le programme d'installation génère des journaux résumés et détaillés, ainsi que des journaux supplémentaires si besoin est. Le programme d'installation est appelé au moins trois fois par action d'installation demandée par l'utilisateur.  
  
 Les fichiers de banque de données contiennent un instantané de l'état de tous les objets de configuration qui sont suivis par le processus d'installation et qui sont utiles pour réparer les erreurs de configuration. Des vidages de fichiers XML sont créés pour les objets de banque de données pour chaque phase d'exécution. Ils sont enregistrés dans leur propre sous-dossier de journal sous le dossier de journal horodaté, comme suit :  
  
-   Datastore_GlobalRules  
  
-   Datastore_ComponentUpdated  
  
-   Datastore  
  
 Les sections suivantes décrivent les fichiers journaux d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="summary-text"></a>Texte de résumé  
  
### <a name="overview"></a>Vue d'ensemble  
 Ce fichier montre les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] détectés au cours de l'installation, l'environnement du système d'exploitation, les valeurs des paramètres de ligne de commande (si elles sont spécifiées) et l'état d'ensemble de chaque fichier MSI/MSP exécuté.  
  
 Le journal comprend les sections suivantes :  
  
-   un résumé d'ensemble de l'exécution ;  
  
-   les propriétés et la configuration de l'ordinateur sur lequel le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a été exécuté ;  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] précédemment installées sur l'ordinateur ;  
  
-   la description des propriétés de la version d'installation et du package d'installation ;  
  
-   les paramètres d'entrée d'exécution fournis au cours de l'installation ;  
  
-   l'emplacement du fichier de configuration ;  
  
-   les détails des résultats d'exécution ;  
  
-   les règles globales ;  
  
-   les règles spécifiques au scénario d'installation ;  
  
-   les règles ayant échoué ;  
  
-   l'emplacement du fichier du rapport de règles.  
  
### <a name="location"></a>Emplacement  
 Il se trouve à l’emplacement %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\.  
  
 Pour trouver les erreurs dans le fichier texte résumé, recherchez les mots clés « error » ou « failed » dans le fichier.  
  
## <a name="summaryengine-baseyyyymmddhhmmsstxt"></a>Summary_engine-base_YYYYMMDD_HHMMss.txt  
  
### <a name="overview"></a>Vue d'ensemble  
 Le fichier de base summary_engine est semblable au fichier résumé et est généré au cours du flux de travail principal.  
  
### <a name="location"></a>Emplacement  
 Il se trouve à l’emplacement %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<AAAAMMJJ_HHMM>\\.  
  
## <a name="summaryengine-baseyyyymmddhhmmsscomponentupdatetxt"></a>Summary_engine-base_YYYYMMDD_HHMMss_ComponentUpdate.txt  
  
### <a name="overview"></a>Vue d'ensemble  
 Le fichier journal résumé de mise à jour des composants est semblable au fichier résumé et est généré au cours du flux de travail de mise à jour des composants.  
  
### <a name="location"></a>Emplacement  
 Il se trouve à l’emplacement %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<AAAAMMJJ_HHMM>\\.  
  
## <a name="summaryengine-baseversionnumbermmddhhmmssglobalrulestxt"></a>Summary_engine-base_\<numéro_version>MMJJ_HHMMss_GlobalRules.txt  
  
### <a name="overview"></a>Vue d'ensemble  
 Le fichier journal résumé des règles globales est semblable au fichier résumé généré au cours du flux de travail des règles globales.  
  
### <a name="location"></a>Emplacement  
 Il se trouve à l’emplacement %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<AAAAMMJJ_HHMM>\\.  
  
## <a name="detailtxt"></a>Detail.txt  
  
### <a name="overview"></a>Vue d'ensemble  
 Detail.txt est généré pour le flux de travail principal, par exemple l'installation ou la mise à niveau, et fournit les détails de l'exécution. Les journaux dans le fichier sont générés en fonction de l'heure à laquelle chaque action pour l'installation a été appelée, et indiquent l'ordre dans lequel les actions ont été exécutées et leurs dépendances.  
  
### <a name="location"></a>Emplacement  
 Il se trouve à l’emplacement %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup  
  
 Bootstrap\Log\\<AAAAMMJJ_HHMM>\Detail.txt.  
  
 Si une erreur se produit au cours du processus d'installation, l'exception ou l'erreur est journalisée à la fin de ce fichier. Pour trouver les erreurs dans ce fichier, examinez d'abord la fin du fichier, puis lancez une recherche sur les mots clés « error » ou « exception » dans le fichier.  
  
## <a name="detailcomponentupdatetxt"></a>Detail_ComponentUpdate.txt  
  
### <a name="overview"></a>Vue d'ensemble  
 Le fichier Detail_ComponentUpdate.txt est généré pour le flux de travail de mise à jour des composants et est semblable au fichier Detail.txt.  
  
### <a name="location"></a>Emplacement  
 Il se trouve à l’emplacement %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<AAAAMMJJ_HHMM>\\.  
  
## <a name="detailglobalrulestxt"></a>Detail_GlobalRules.txt  
  
### <a name="overview"></a>Vue d'ensemble  
 Le fichier Detail_GlobalRules.txt est généré pour l'exécution des règles globales et est semblable au fichier Detail.txt.  
  
### <a name="location"></a>Emplacement  
 Il se trouve à l’emplacement %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<AAAAMMJJ_HHMM>\\.  
  
## <a name="msi-log-files"></a>Fichiers journaux MSI  
  
### <a name="overview"></a>Vue d'ensemble  
 Les fichiers journaux MSI fournissent des détails sur le processus du package d'installation. Ils sont générés par le programme MSIEXEC lors de l'installation du package spécifié.  
  
 Types de fichiers journaux MSI :  
  
-   \<Fonctionnalité>_\<Architecture>\_\<Interaction>.log  
  
-   \<Fonctionnalité>_\<Architecture>\_\<Langue\_\<Interaction>.log  
  
-   \<Fonctionnalité>_\<Architecture>\_\<Interaction>\_\<FLux_de_travail>.log  
  
### <a name="location"></a>Emplacement  
 Les fichiers journaux MSI se trouvent à l’emplacement %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<AAAAMMJJ_HHMM>\\<nom\>.log.  
  
 À la fin du fichier se trouve un résumé de l'exécution qui indique l'état de réussite ou d'échec et les propriétés. Pour trouver l'erreur dans le fichier MSI, recherchez « value 3 ». Les erreurs se trouvent généralement à proximité de cette chaîne.  
  
## <a name="configurationfileini"></a>ConfigurationFile.ini  
  
### <a name="overview"></a>Vue d'ensemble  
 Le fichier de configuration contient les paramètres d'entrée fournis au cours de l'installation. Vous pouvez l'utiliser pour redémarrer l'installation sans entrer les paramètres manuellement. Toutefois, les mots de passe pour les comptes, PID et certains paramètres ne sont pas enregistrés dans le fichier de configuration. Les paramètres peuvent être soit ajoutés au fichier, soit fournis à l'aide de la ligne de commande ou de l'interface utilisateur du programme d'installation. Pour plus d’informations, consultez [Installer SQL Server 2016 à l’aide d’un fichier de configuration](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md).  
  
### <a name="location"></a>Emplacement  
 Il se trouve à l’emplacement %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<AAAAMMJJ_HHMM>\\.  
  
## <a name="systemconfigurationcheckreporthtm"></a>SystemConfigurationCheck_Report.htm  
  
### <a name="overview"></a>Vue d'ensemble  
 Le rapport de vérification de la configuration du système contient une brève description de chaque rôle exécuté et de l'état d'exécution.  
  
### <a name="location"></a>Emplacement  
 Il se trouve à l’emplacement %programfiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\130\Setup Bootstrap\Log\\<AAAAMMJJ_HHMM>\\.  
  
## <a name="see-also"></a>Voir aussi  
 [Installer SQL Server 2016](../../database-engine/install-windows/install-sql-server.md)  
  
  

