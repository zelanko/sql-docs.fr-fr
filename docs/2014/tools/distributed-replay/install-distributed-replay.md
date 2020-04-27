---
title: Installer Distributed Replay à partir de l’invite de commandes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ea1171da-f50e-4f16-bedc-5e468a46477f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 67d74db6faf9b40ad323ed2948c2c0a596a63016
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63149718"
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
|Outil d'administration|**outils**|  
  
> [!IMPORTANT]  
>  Une fois que vous avez installé Distributed Replay, vous devez créer des règles de pare-feu sur le contrôleur et les ordinateurs clients, et accorder des autorisations à chaque ordinateur client sur le serveur cible. Pour plus d’informations, consultez [Suivre les étapes consécutives à l’installation](complete-the-post-installation-steps.md).  
  
 Utilisez les paramètres répertoriés dans le tableau ci-dessous pour développer des scripts d'installation en ligne de commande.  
  
|Paramètre|Description|Valeurs prises en charge|  
|---------------|-----------------|----------------------|  
|/CTLRSVCACCOUNT<br /><br /> **Facultatif**|Compte de service Distributed Replay Controller.|Vérifie le compte et le mot de passe|  
|/CTLRSVCPASSWORD<br /><br /> **Facultatif**|Mot de passe du compte de service Distributed Replay Controller.|Vérifie le compte et le mot de passe|  
|/CTLRSTARTUPTYPE<br /><br /> **Facultatif**|Type de démarrage pour le compte de service Distributed Replay Controller.|Automatique<br /><br /> Désactivé<br /><br /> Manuelle|  
|/CTLRUSERS<br /><br /> **Facultatif**|Spécifiez les utilisateurs qui disposent d'autorisations pour le service Distributed Replay Controller.|Ensemble de chaînes de compte d'utilisateur utilisant «   » (espace) comme séparateur<br /><br /> **Important**: lorsque vous configurez le service Distributed Replay Controller, vous pouvez spécifier un ou plusieurs comptes d'utilisateurs qui seront utilisés pour exécuter les services Distributed Replay Client. Vous trouverez ci-dessous la liste des comptes pris en charge :<br /><br /> Compte d’utilisateur de domaine<br /><br /> Compte d'utilisateur local créé par l'utilisateur<br /><br /> Administrateur<br /><br /> Compte virtuel et Compte de service administré (MSA)<br /><br /> Services réseau, Services locaux et Système<br /><br /> <br /><br /> Les comptes de groupe (locaux ou de domaine) et autres comptes intégrés (comme Tout le monde) ne sont pas acceptés.|  
|/CLTSVCACCOUNT<br /><br /> **Facultatif**|Compte de service Distributed Replay Client.|Vérifie le compte et le mot de passe|  
|/CLTSVCPASSWORD<br /><br /> **Facultatif**|Mot de passe du compte du service Distributed Replay Client.|Vérifie le compte et le mot de passe|  
|/CLTSTARTUPTYPE<br /><br /> **Facultatif**|Type de démarrage du compte du service Distributed Replay Client.|Automatique<br /><br /> Désactivé<br /><br /> Manuelle|  
|/CLTCTLRNAME<br /><br /> **Facultatif**|Nom de l'ordinateur avec lequel le client communique pour le service Distributed Replay Controller.||  
|/CLTWORKINGDIR<br /><br /> **Facultatif**|Répertoire de travail du service Distributed Replay Client.|Chemin d'accès valide|  
|/CLTRESULTDIR<br /><br /> **Facultatif**|Répertoire des résultats du service Distributed Replay Client.|Chemin d'accès valide|  
  
### <a name="sample-syntax"></a>Exemple de syntaxe :  
 **Pour installer le composant contrôleur de Distributed Replay**  
  
```  
setup /q /ACTION=Install /FEATURES=DREPLAY_CTLR /IAcceptSQLServerLicenseTerms /CTLRUSERS="domain\user1" "domain\user2" /CTLRSVCACCOUNT="domain\svcuser" /CTLRSVCPASSWORD="password" /CTLRSTARTUPTYPE=Automatic  
```  
  
 **Pour installer le composant client de Distributed Replay**  
  
```  
setup /q /ACTION=Install /FEATURES=DREPLAY_CLT /IAcceptSQLServerLicenseTerms /CLTSVCACCOUNT="domain\svcuser" /CLTSVCPASSWORD="password" /CLTSTARTUPTYPE=Automatic /CLTCTLRNAME=ControllerMachineName /CLTWORKINGDIR="C:\WorkingDir" /CLTRESULTDIR="C:\ResultDir  
```  
  
  
