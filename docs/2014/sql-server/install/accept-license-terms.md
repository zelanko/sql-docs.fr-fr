---
title: Accepter les termes du contrat de licence | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- license terms
helpviewer_keywords:
- Registration Information page [SQL Server Installation Wizard]
- SQL Server Installation Wizard, Registration Information page
ms.assetid: 08dd739d-5817-4418-bcff-74ab7f8bbd33
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 99418b11eecdb3077e3def746eae56e43bab2d60
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66096838"
---
# <a name="accept-license-terms"></a>Accepter les termes du contrat de licence
  Utilisez la page **Accepter les termes du contrat de licence** de l’Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour accepter les ter.mes du contrat de licence de cette version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Vous pouvez imprimer le contrat de licence ou le copier dans le Presse-papiers. Pour continuer, acceptez le contrat de licence, puis cliquez sur **Suivant**. Pour quitter l’installation, cliquez sur **Annuler**.  
  
## <a name="customer-experience-improvement-program-ceip"></a>Customer Experience Improvement Program (CEIP)  
 Si vous activez la création de rapports CEIP, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour envoyer régulièrement un rapport à [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Ces rapports incluent des informations sur votre configuration matérielle et sur la façon dont vous utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les composants. [!INCLUDE[msCoName](../../includes/msconame-md.md)] utilise les données sur l'utilisation des fonctionnalités pour améliorer les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les composants suivants font partie des composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] analysés :  
  
-   Le [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   Réplication  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Programme d'installation  
  
 Les informations sur l'utilisation des fonctionnalités sont envoyées à [!INCLUDE[msCoName](../../includes/msconame-md.md)], puis stockées avec un accès limité.  
  
 Pour désactiver la création de rapports CEIP une fois l’installation terminée, utilisez l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] outil rapports d’erreurs et d’utilisation** dans le menu outils de **configuration** .  
  
 Pour les actions du programme d'installation, telles que l'installation, la mise à niveau, la réparation, entre autres, les informations sont recueillies et téléchargées uniquement pendant l'exécution du programme d'installation  
  
 Pour tous les autres composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , les informations sont recueillies une fois par jour pour toutes les instances activées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par défaut, la collecte est effectuée à minuit afin de réduire la charge sur le serveur. Si vous souhaitez changer l'heure de la collecte, vous pouvez modifier manuellement la clé du Registre concernée. Chaque instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] possède sa propre clé de Registre :  
  
 \\[!INCLUDE[msCoName](../../includes/msconame-md.md)]HKLM\Software\\\MSSQL12.[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<InstanceId> \cpe\timeofreporting  
  
 La valeur de cette clé de Registre inclut l'heure de la collecte ainsi que le nombre de minutes qui s'écoulent à partir de 00:00 (minuit). Par exemple, la valeur 60 fixe l'exécution de la collecte à 1:00 a.m., la valeur 1200 fixe l'exécution de la collecte à 8:00 p.m., et ainsi de suite.  
  
## <a name="error-reporting"></a>Rapport d'erreurs  
 Utilisez la page **Paramètres de rapports d’erreurs et d’utilisation** de l’Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour activer la fonctionnalité de création de rapports d’erreurs et d’utilisation dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="options"></a>Options  
 Par défaut, les fonctionnalités de rapport d'erreurs et de collecte des données d'utilisation des fonctionnalités sont désactivées pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et ses composants dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Rapport d'erreurs  
 Si vous activez la fonctionnalité Rapport d'erreurs, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour envoyer automatiquement un rapport à [!INCLUDE[msCoName](../../includes/msconame-md.md)] si une erreur irrécupérable se produit dans l'un des composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] suivants :  
  
-   Le [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   Réplication  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] utilise les rapports d'erreurs pour améliorer le fonctionnement de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ces informations sont traitées en toute confidentialité.  
  
 Des informations sur les erreurs sont envoyées à [!INCLUDE[msCoName](../../includes/msconame-md.md)]par le biais d'une connexion sécurisée (https) et elles sont stockées avec un accès limité. Des rapports d'erreurs peuvent également être envoyés sur votre propre serveur de rapports d'erreurs d'entreprise.  
  
 Les rapports d'erreurs comprennent les informations suivantes :  
  
-   la condition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lorsque le problème s'est produit ;  
  
-   des informations sur la version du système d'exploitation et le matériel ;  
  
-   votre ID de produit numérique, qui n'est pas utilisé pour identifier votre licence ;  
  
-   l'adresse IP réseau de votre ordinateur ou de votre serveur proxy ;  
  
-   des informations provenant de la mémoire ou des fichiers du processus à l'origine de l'erreur.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ne regroupe pas de manière intentionnelle vos fichiers, nom, adresse, adresse électronique ou tout autre forme d'informations personnelles. Le rapport d'erreurs peut toutefois contenir des informations personnelles qui proviennent de la mémoire ou des fichiers du processus à l'origine de l'erreur. Bien que ces informations permettent à priori de déterminer votre identité, [!INCLUDE[msCoName](../../includes/msconame-md.md)] ne les exploite pas à cette fin.  
  
 Pour plus d’informations sur la politique de confidentialité et la procédure de collecte de données de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez la [déclaration de confidentialité de Microsoft SQL Server](../../../2014/getting-started/microsoft-sql-server-privacy-statement.md).  
  
 Si vous activez les rapports d'erreurs et qu'une erreur irrécupérable se produit, vous pouvez voir une réponse de [!INCLUDE[msCoName](../../includes/msconame-md.md)] dans le journal des événements Windows, qui pointe sur un article de la Base de connaissances [!INCLUDE[msCoName](../../includes/msconame-md.md)] traitant cette erreur.  
  
 Pour désactiver la fonction de rapport d’erreurs et d’utilisation de fonctionnalités pour toutes les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et leurs composants une fois l’installation terminée, accédez à la boîte de dialogue **Paramètres de rapports d’erreurs et d’utilisation** et décochez les cases pour **Utilisation de fonctionnalités**. Si le **rapport d’erreurs** est activé pour plusieurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] composants de [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]( [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]composants [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]partagés,, et), vous pouvez désactiver le rapport d’erreurs pour chaque instance d’un composant individuel, ainsi que les composants partagés, listés comme **autres**.  
  
## <a name="see-also"></a>Voir aussi  
 [À propos des termes du contrat de licence SQL Server](../../../2014/getting-started/about-the-sql-server-license-terms.md)  
  
  
