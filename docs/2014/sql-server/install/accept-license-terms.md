---
title: Acceptez les termes du contrat de licence | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
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
ms.openlocfilehash: 631ae416116832c725de8335780db87c03811320
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48141559"
---
# <a name="accept-license-terms"></a>Accepter les termes du contrat de licence
  Utilisez le **accepter les termes du contrat de licence** page de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Installation pour accepter les termes du contrat de licence pour cette version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Vous pouvez imprimer le contrat de licence ou le copier dans le Presse-papiers. Pour continuer, acceptez le contrat de licence, puis cliquez sur **Suivant**. Pour quitter l’installation, cliquez sur **Annuler**.  
  
## <a name="customer-experience-improvement-program-ceip"></a>Customer Experience Improvement Program (CEIP)  
 Si vous activez la création de rapports CEIP, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour envoyer régulièrement un rapport à [!INCLUDE[msCoName](../../includes/msconame-md.md)]. Ces rapports incluent des informations sur votre configuration matérielle et sur la façon dont vous utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les composants. [!INCLUDE[msCoName](../../includes/msconame-md.md)] utilise les données sur l'utilisation des fonctionnalités pour améliorer les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les composants suivants font partie des composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] analysés :  
  
-   Le [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   REPLICATION  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Programme d’installation  
  
 Plus d’informations sur l’utilisation des fonctionnalités sont envoyés à [!INCLUDE[msCoName](../../includes/msconame-md.md)], où elles sont stockées avec un accès limité.  
  
 Pour désactiver la création de rapports CEIP une fois l’installation terminée, utilisez le  **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] rapports d’erreurs et l’utilisation** outil sur le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **outils de Configuration** menu.  
  
 Pour les actions du programme d'installation, telles que l'installation, la mise à niveau, la réparation, entre autres, les informations sont recueillies et téléchargées uniquement pendant l'exécution du programme d'installation  
  
 Pour tous les autres composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les informations sont recueillies une fois par jour pour toutes les instances activées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par défaut, la collecte est effectuée à minuit afin de réduire la charge sur le serveur. Si vous souhaitez changer l'heure de la collecte, vous pouvez modifier manuellement la clé du Registre concernée. Chaque instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a sa propre clé de Registre :  
  
 HKLM\Software\\[!INCLUDE[msCoName](../../includes/msconame-md.md)]\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.\< ID_INSTANCE > \CPE\TimeofReporting  
  
 La valeur de cette clé de Registre inclut l'heure de la collecte ainsi que le nombre de minutes qui s'écoulent à partir de 00:00 (minuit). Par exemple, la valeur 60 fixe l'exécution de la collecte à 1:00 a.m., la valeur 1200 fixe l'exécution de la collecte à 8:00 p.m., et ainsi de suite.  
  
## <a name="error-reporting"></a>Rapport d'erreurs  
 Utilisez le **erreur et les paramètres de rapport d’utilisation** page de la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Installation pour activer les erreurs de fonctionnalité et des fonctionnalités pour des rapports d’utilisation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="options"></a>Options  
 Par défaut, la collecte des données d’utilisation des fonctionnalités et les fonctionnalités de rapport d’erreurs sont désactivées pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et ses composants dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Rapport d'erreurs  
 Si vous activez la fonctionnalité rapport d’erreurs, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est configuré pour envoyer un rapport à [!INCLUDE[msCoName](../../includes/msconame-md.md)] automatiquement si une erreur irrécupérable se produit dans un des éléments suivants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] composants :  
  
-   Le [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   REPLICATION  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] utilise les rapports d’erreurs pour améliorer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonctionnalité et traite toutes les informations comme confidentielles.  
  
 Des informations sur les erreurs sont envoyées à [!INCLUDE[msCoName](../../includes/msconame-md.md)] par le biais d'une connexion sécurisée (https) et elles sont stockées avec un accès limité. Des rapports d'erreurs peuvent également être envoyés sur votre propre serveur de rapports d'erreurs d'entreprise.  
  
 Les rapports d'erreurs comprennent les informations suivantes :  
  
-   La condition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] lorsque le problème s’est produite.  
  
-   des informations sur la version du système d'exploitation et le matériel ;  
  
-   votre ID de produit numérique, qui n'est pas utilisé pour identifier votre licence ;  
  
-   l'adresse IP réseau de votre ordinateur ou de votre serveur proxy ;  
  
-   des informations provenant de la mémoire ou des fichiers du processus à l'origine de l'erreur.  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ne collecte pas intentionnellement vos fichiers, nom, adresse, adresse de messagerie ou toute autre forme d’informations personnelles. Le rapport d'erreurs peut toutefois contenir des informations personnelles qui proviennent de la mémoire ou des fichiers du processus à l'origine de l'erreur. Bien que ces informations permettent à priori de déterminer votre identité, [!INCLUDE[msCoName](../../includes/msconame-md.md)] ne les exploite pas à cette fin.  
  
 Pour plus d’informations sur la [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] confidentialité et la stratégie de collecte de données, consultez [déclaration de confidentialité de Microsoft SQL Server](../../../2014/getting-started/microsoft-sql-server-privacy-statement.md).  
  
 Si vous activez les rapports d'erreurs et qu'une erreur irrécupérable se produit, vous pouvez voir une réponse de [!INCLUDE[msCoName](../../includes/msconame-md.md)] dans le journal des événements Windows, qui pointe sur un article de la Base de connaissances [!INCLUDE[msCoName](../../includes/msconame-md.md)] traitant cette erreur.  
  
 Pour désactiver le rapport d’erreur ou d’utilisation des fonctionnalités pour toutes les instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et leurs composants une fois l’installation terminée, accédez à la **erreur et les paramètres de rapport d’utilisation** boîte de dialogue et désactivez les cases à cocher pour **l’utilisation des fonctionnalités** . Si **rapport d’erreurs** est activée pour plusieurs composants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]et les composants partagés) vous pouvez désactiver le rapport d’erreurs pour chaque instance d’un individu composant, ainsi que des composants partagés, répertorié comme **d’autres**.  
  
## <a name="see-also"></a>Voir aussi  
 [À propos des termes du contrat de licence SQL Server](../../../2014/getting-started/about-the-sql-server-license-terms.md)  
  
  
