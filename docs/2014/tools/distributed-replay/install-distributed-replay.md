---
title: Installer Distributed Replay à partir de l’invite de commandes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: ea1171da-f50e-4f16-bedc-5e468a46477f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d7dbc86ff32e0c9ba6e77558a713cda2598221e0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126119"
---
# <a name="install-distributed-replay-from-the-command-prompt"></a>Installer Distributed Replay à partir de l'invite de commandes
  L'installation d'une nouvelle instance de Distributed Replay à partir de l'invite de commandes vous permet de spécifier les composants à installer et la façon dont ils doivent être configurés. L'installation par l'invite de commandes prend en charge l'installation, la réparation, la mise à niveau et la désinstallation des composants Distributed Replay. Lors de l'installation à partir de l'invite de commandes, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge le mode silencieux complet via le paramètre /Q.  
  
> [!NOTE]  
>  Pour des installations locales, vous devez exécuter le programme d'installation en tant qu'administrateur. Si vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'un partage distant, vous devez utiliser un compte de domaine qui a les autorisations de lecture et d'exécution sur le partage distant.  
  
## <a name="installation-parameters"></a>Paramètres d'installation  
 La liste des fonctionnalités prioritaires comprend [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]et Tools. La fonctionnalité Tools installera les outils d'administration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ainsi que d'autres composants partagés. Pour installer les composants Distributed Replay, spécifiez les paramètres suivants :  
  
|Composant|Paramètre|  
|---------------|---------------|  
|Distributed Replay Controller|**DREPLAY_CTLR**|  
|Distributed Replay Client|**DREPLAY_CLT**|  
|Outil d'administration|**Outils**|  
  
> [!IMPORTANT]  
>  Une fois que vous avez installé Distributed Replay, vous devez créer des règles de pare-feu sur le contrôleur et les ordinateurs clients, et accorder des autorisations à chaque ordinateur client sur le serveur cible. Pour plus d’informations, consultez [Suivre les étapes consécutives à l’installation](complete-the-post-installation-steps.md).  
  
 Utilisez les paramètres répertoriés dans le tableau ci-dessous pour développer des scripts d'installation en ligne de commande.  
  
|Paramètre|Description|Valeurs prises en charge|  
|---------------|-----------------|----------------------|  
|/CTLRSVCACCOUNT<br /><br /> **Ce paramètre est facultatif**|Compte de service Distributed Replay Controller.|Vérifie le compte et le mot de passe|  
|/CTLRSVCPASSWORD<br /><br /> **Ce paramètre est facultatif**|Mot de passe du compte de service Distributed Replay Controller.|Vérifie le compte et le mot de passe|  
|/CTLRSTARTUPTYPE<br /><br /> **Ce paramètre est facultatif**|Type de démarrage pour le compte de service Distributed Replay Controller.|Automatic<br /><br /> Désactivé<br /><br /> Manuel|  
|/CTLRUSERS<br /><br /> **Ce paramètre est facultatif**|Spécifiez les utilisateurs qui disposent d'autorisations pour le service Distributed Replay Controller.|Ensemble de chaînes de compte d'utilisateur utilisant «   » (espace) comme séparateur<br /><br /> **Important**: lorsque vous configurez le service Distributed Replay Controller, vous pouvez spécifier un ou plusieurs comptes d'utilisateurs qui seront utilisés pour exécuter les services Distributed Replay Client. Vous trouverez ci-dessous la liste des comptes pris en charge :<br /><br /> Compte d'utilisateur de domaine<br /><br /> Compte d'utilisateur local créé par l'utilisateur<br /><br /> Administrateur<br /><br /> Compte virtuel et Compte de service administré (MSA)<br /><br /> Services réseau, Services locaux et Système<br /><br /> <br /><br /> Les comptes de groupe (locaux ou de domaine) et autres comptes intégrés (comme Tout le monde) ne sont pas acceptés.|  
|/CLTSVCACCOUNT<br /><br /> **Ce paramètre est facultatif**|Compte de service Distributed Replay Client.|Vérifie le compte et le mot de passe|  
|/CLTSVCPASSWORD<br /><br /> **Ce paramètre est facultatif**|Mot de passe du compte du service Distributed Replay Client.|Vérifie le compte et le mot de passe|  
|/CLTSTARTUPTYPE<br /><br /> **Ce paramètre est facultatif**|Type de démarrage du compte du service Distributed Replay Client.|Automatic<br /><br /> Désactivé<br /><br /> Manuel|  
|/CLTCTLRNAME<br /><br /> **Ce paramètre est facultatif**|Nom de l'ordinateur avec lequel le client communique pour le service Distributed Replay Controller.||  
|/CLTWORKINGDIR<br /><br /> **Ce paramètre est facultatif**|Répertoire de travail du service Distributed Replay Client.|Chemin d'accès valide|  
|/CLTRESULTDIR<br /><br /> **Ce paramètre est facultatif**|Répertoire des résultats du service Distributed Replay Client.|Chemin d'accès valide|  
  
### <a name="sample-syntax"></a>Exemple de syntaxe :  
 **Pour installer le composant contrôleur de Distributed Replay**  
  
```  
setup /q /ACTION=Install /FEATURES=DREPLAY_CTLR /IAcceptSQLServerLicenseTerms /CTLRUSERS="domain\user1" "domain\user2" /CTLRSVCACCOUNT="domain\svcuser" /CTLRSVCPASSWORD="password" /CTLRSTARTUPTYPE=Automatic  
```  
  
 **Pour installer le composant client de Distributed Replay**  
  
```  
setup /q /ACTION=Install /FEATURES=DREPLAY_CLT /IAcceptSQLServerLicenseTerms /CLTSVCACCOUNT="domain\svcuser" /CLTSVCPASSWORD="password" /CLTSTARTUPTYPE=Automatic /CLTCTLRNAME=ControllerMachineName /CLTWORKINGDIR="C:\WorkingDir" /CLTRESULTDIR="C:\ResultDir  
```  
  
  
