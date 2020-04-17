---
title: Sécurité d’accès au Code d’intégration CLR (fr) Microsoft Docs
description: Pour l’intégration SQL Server CLR, CLR prend en charge la sécurité d’accès au code pour le code géré, lorsque des autorisations sont accordées aux assemblages basés sur l’identité du code.
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- UNSAFE assemblies
- permissions [CLR integration]
- common language runtime [SQL Server], security
- SAFE assemblies
- code access security [CLR integration]
- EXTERNAL_ACCESS assemblies
ms.assetid: 2111cfe0-d5e0-43b1-93c3-e994ac0e9729
author: rothja
ms.author: jroth
ms.openlocfilehash: 912db3acb6f6dc21952e99da31a1484a9745ed0b
ms.sourcegitcommit: b2cc3f213042813af803ced37901c5c9d8016c24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81488308"
---
# <a name="clr-integration-code-access-security"></a>Sécurité d'accès du code de l'intégration du CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L’heure courante de l’exécution de la langue (CLR) prend en charge un modèle de sécurité appelé sécurité d’accès au code pour le code géré. Dans ce modèle, les autorisations sont accordées aux assemblys selon l'identité du code. Pour plus d'informations, consultez la section relative à la sécurité d'accès du code dans le kit de développement logiciel (SDK) .NET Framework.  
  
 La stratégie de sécurité qui détermine les autorisations accordée aux assemblys est définie dans trois emplacements différents :  
  
-   Stratégie de l'ordinateur : il s'agit de la stratégie appliquée pour tout le code managé qui s'exécute sur l'ordinateur sur lequel [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est installé.  
  
-   Stratégie de l'utilisateur : il s'agit de la stratégie appliquée pour le code managé hébergé par un processus. Pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], la stratégie de l'utilisateur est spécifique au compte Windows sur lequel le service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] s'exécute.  
  
-   Stratégie de l'hôte : il s'agit de la stratégie configurée par l'hôte du CLR (dans ce cas, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) qui est appliquée pour le code managé qui s'exécute sur cet hôte.  
  
 Le mécanisme de sécurité d'accès du code pris en charge par le CLR est basé sur la supposition que le module d'exécution peut héberger à la fois du code d'un niveau de confiance total et d'un niveau de confiance partiel. Les ressources protégées par la sécurité d'accès du code CLR sont généralement intégrées à des interfaces de programmation d'applications managées qui requièrent l'autorisation correspondante avant d'accorder l'accès à la ressource. La demande d'autorisation est satisfaite seulement si tous les appelants (au niveau de l'assembly) de la pile d'appels ont l'autorisation pour la ressource correspondante.  
  
 Le jeu d'autorisations de sécurité d'accès du code accordées au code managé en cas d'exécution à l'intérieur de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est l'intersection du jeu d'autorisations accordées par les trois niveaux de stratégie précités. Même si [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] accorde un jeu d'autorisations à un assembly chargé dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], le jeu éventuel d'autorisations accordées au code utilisateur peut être restreint davantage par les stratégies de l'utilisateur et de l'ordinateur.  
  
## <a name="sql-server-host-policy-level-permission-sets"></a>Jeux d'autorisations au niveau stratégie de l'hôte de SQL Server  
 Le jeu d'autorisations de sécurité d'accès du code accordées aux assemblys par le niveau de stratégie de l'hôte [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est déterminé par le jeu d'autorisations spécifié lors de la création de l'assembly. Il existe trois ensembles d’autorisation : **SAFE**, **EXTERNAL_ACCESS** et **UNSAFE** (spécifié en utilisant **l’option PERMISSION_SET** de CREATE ASSEMBLY [&#40;Transact-SQL&#41;](../../../t-sql/statements/create-assembly-transact-sql.md)).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournit un niveau de stratégie de sécurité au niveau de l'hôte au CLR (Common Language Runtime) quand il l'héberge ; cette stratégie est un niveau de stratégie supplémentaire sous les deux niveaux de stratégie qui sont toujours effectifs. Cette stratégie est définie pour chaque domaine d'application qui est créé par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Cette stratégie n'est pas destinée au domaine d'application par défaut appliqué lorsque [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] crée une instance du CLR.  
  
 La stratégie de niveau hôte de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est une combinaison de la stratégie fixe de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour les assemblys système et de la stratégie spécifiée par l’utilisateur pour les assemblys utilisateur.  
  
 La stratégie fixe pour les assemblys CLR et les assemblys système [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] leur accorde une confiance totale.  
  
 La partie spécifiée par l'utilisateur de la stratégie de l'hôte [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est basée sur le propriétaire de l'assembly spécifiant un des trois compartiments d'autorisation pour chaque assembly. Pour plus d'informations sur les autorisations de sécurité répertoriées ci-dessous, consultez le kit de développement logiciel SDK .NET Framework.  
  
### <a name="safe"></a>SAFE  
 Seuls le calcul interne et l’accès aux données locales sont autorisés. **SAFE** est l’ensemble d’autorisations le plus restrictif. Le code exécuté par un assemblage avec des autorisations **SAFE** ne peut pas accéder aux ressources externes du système telles que les fichiers, le réseau, les variables de l’environnement ou le registre.  
  
 **Les** assemblages SAFE ont les autorisations et les valeurs suivantes :  
  
|Autorisation|Valeur(s)/description|  
|----------------|-----------------------------|  
|**Securitypermission**|**Exécution:** Permission d’exécuter le code géré.|  
|**SqlClientPermission**|**Connexion contextuelle - vrai,** **connexion contextuelle - oui**: seule la connexion contextuelle peut être utilisée et la chaîne de connexion ne peut que spécifier une valeur de " connexion contextuelle " ou de " connexion contextuelle -oui ".<br /><br /> **AllowBlankPassword - faux:**  Les mots de passe vierges ne sont pas autorisés.|  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 EXTERNAL_ACCESS assemblées ont les mêmes autorisations que les assemblages **SAFE,** avec la capacité supplémentaire d’accéder aux ressources externes du système telles que les fichiers, les réseaux, les variables environnementales et le registre.  
  
 **EXTERNAL_ACCESS** assemblées ont également les autorisations et les valeurs suivantes :  
  
|Autorisation|Valeur(s)/description|  
|----------------|-----------------------------|  
|**DistributedTransactionPermission**|**Sans restriction:** Les transactions distribuées sont autorisées.|  
|**DNSPermission (en)**|**Sans restriction:** Permission de demander des informations auprès de Domain Name Servers.|  
|**EnvironnementPermission**|**Sans restriction:** L’accès complet aux variables du système et de l’environnement utilisateur est autorisé.|  
|**EventLogPermission**|**Administrer :** Les actions suivantes sont autorisées : création d’une source d’événement, lecture des journaux existants, suppression des sources ou des journaux d’événements, réponse aux entrées, effacement d’un journal d’événements, écoute des événements et accès à une collection de tous les journaux d’événements.|  
|**FileIOPermission**|**Sans restriction:** L’accès complet aux fichiers et dossiers est autorisé.|  
|**KeyContainerPermission (keyContainerPermission)**|**Sans restriction:** L’accès complet aux conteneurs clés est autorisé.|  
|**Information réseauPermission**|**Accès:** Le ping est autorisé.|  
|**RegistrePermission**|Permet de lire les droits de **HKEY_CLASSES_ROOT**, **HKEY_LOCAL_MACHINE**, **HKEY_CURRENT_USER**, **HKEY_CURRENT_CONFIG**, et **HKEY_USERS.**|  
|**Securitypermission**|**Affirmation:** Capacité d’affirmer que tous les appelants de ce code ont la permission requise pour l’opération.<br /><br /> **ContrôlePrincipal:** Capacité de manipuler l’objet principal.<br /><br /> **Exécution:** Permission d’exécuter le code géré.<br /><br /> **SérialisationFormatter:** Capacité de fournir des services de sérialisation.|  
|**SmtpPermission**|**Accès:** Les liaisons sortantes vers le port hôte SMTP 25 sont autorisées.|  
|**SocketPermission (SocketPermission)**|**Connectez-vous:** Les liaisons sortantes (tous les ports, tous les protocoles) sur une adresse de transport sont autorisées.|  
|**SqlClientPermission**|**Sans restriction:** L’accès complet à la source de données est autorisé.|  
|**StorePermission (en)**|**Sans restriction:** L’accès complet aux magasins de certificat X.509 est autorisé.|  
|**WebPermission**|**Connectez-vous:** Les connexions sortantes aux ressources Web sont autorisées.|  
  
### <a name="unsafe"></a>UNSAFE  
 UNSAFE offre aux assemblies un accès sans restriction aux ressources, à la fois à l'intérieur et à l'extérieur de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le code exécutant à partir d’un assemblage **UNSAFE** peut également appeler le code non menté.  
  
 **Les** assemblages UNSAFE sont donnés **FullTrust**.  
  
> [!IMPORTANT]  
>  **SAFE** est le paramètre d’autorisation recommandé pour les assemblages qui [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]effectuent des tâches de calcul et de gestion des données sans accéder aux ressources à l’extérieur. **EXTERNAL_ACCESS** est recommandé pour les assemblées [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]qui accèdent aux ressources à l’extérieur . **EXTERNAL_ACCESS** assemblages par défaut s’exécutent comme compte de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service. Il est possible pour **EXTERNAL_ACCESS** code d’usurper explicitement l’identité du contexte de sécurité Windows Authentication de l’appelant. Étant donné que la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] valeur par défaut est d’exécuter comme compte de service, l’autorisation d’exécuter **EXTERNAL_ACCESS** ne doit être donnée qu’aux connexions fiables pour fonctionner comme compte de service. Du point de vue de la sécurité, les assemblages **EXTERNAL_ACCESS** et **UNSAFE** sont identiques. Cependant, **les assemblages EXTERNAL_ACCESS** offrent diverses protections de fiabilité et de robustesse qui ne sont pas dans les assemblages **UNSAFE.** Spécifier **UNSAFE** permet au code dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] l’assemblage d’effectuer des opérations illégales contre [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]l’espace de processus, et peut donc potentiellement compromettre la robustesse et l’évolutivité de . Pour plus d’informations sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]la création d’assemblages CLR , voir [Managing CLR Integration Assemblies](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md).  
  
## <a name="accessing-external-resources"></a>Accès aux ressources externes  
 Si un type défini par l’utilisateur (UDT), une procédure stockée ou un autre type d’assemblage de construction est enregistré avec l’ensemble **d’autorisation SAFE,** le code géré exécutant dans la construction n’est pas en mesure d’accéder aux ressources externes. Toutefois, si les ensembles **d’autorisations EXTERNAL_ACCESS** ou **UNSAFE** sont spécifiés [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et que le code géré tente d’accéder aux ressources externes, applique les règles suivantes :  
  
|Si|Alors|  
|--------|----------|  
|Le contexte d'exécution correspond à une connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|Les tentatives d'accéder aux ressources externes sont refusées et une exception de sécurité est levée.|  
|Le contexte d'exécution correspond à une connexion Windows et le contexte d'exécution est l'appelant d'origine.|La ressource externe est accédée sous le contexte de sécurité du compte de service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|L'appelant n'est pas l'appelant d'origine.|L'accès est refusé et une exception de sécurité est levée.|  
|Le contexte d’exécution correspond à une connexion Windows et le contexte d’exécution est l’appelant d’origine et l’appelant a été usurpé par l’appel.|L'accès s'effectue en utilisant le contexte de sécurité de l'appelant, et non le compte de service.|  
  
## <a name="permission-set-summary"></a>Synthèse des jeux d'autorisations  
 Le tableau suivant résume les restrictions et les autorisations accordées aux ensembles **d’autorisation SAFE**, **EXTERNAL_ACCESS**et **UNSAFE.**  
  
|||||  
|-|-|-|-|  
||**Sûr**|**EXTERNAL_ACCESS**|**Dangereux**|  
|**Autorisations de sécurité d’accès au code**|Exécution uniquement|Exécution + accès aux ressources externes|Illimité (y compris P/Invoke)|  
|**Restrictions du modèle de programmation**|Oui|Oui|Aucune restriction|  
|**Vérifiabilité requise**|Oui|Oui|Non|  
|**Accès aux données locales**|Oui|Oui|Oui|  
|**Possibilité d'appeler du code natif**|Non|Non|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité d’intégration CLR](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [Attributs de protection des hôtes et programmation d’intégration CLR](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Restrictions du modèle de programmation d’intégration CLR](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Environnement hébergé CLR](../../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md)  
  
  
