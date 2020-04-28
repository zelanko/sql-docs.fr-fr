---
title: Sécurité d’accès du code d’intégration du CLR | Microsoft Docs
description: Pour SQL Server l’intégration du CLR, CLR prend en charge la sécurité d’accès du code pour le code managé, où les autorisations sont accordées aux assemblys en fonction de l’identité du code.
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81488308"
---
# <a name="clr-integration-code-access-security"></a>Sécurité d'accès du code de l'intégration du CLR
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Le common language runtime (CLR) prend en charge un modèle de sécurité appelé sécurité d’accès du code pour le code managé. Dans ce modèle, les autorisations sont accordées aux assemblys selon l'identité du code. Pour plus d'informations, consultez la section relative à la sécurité d'accès du code dans le kit de développement logiciel (SDK) .NET Framework.  
  
 La stratégie de sécurité qui détermine les autorisations accordée aux assemblys est définie dans trois emplacements différents :  
  
-   Stratégie de l'ordinateur : il s'agit de la stratégie appliquée pour tout le code managé qui s'exécute sur l'ordinateur sur lequel [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est installé.  
  
-   Stratégie de l'utilisateur : il s'agit de la stratégie appliquée pour le code managé hébergé par un processus. Pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], la stratégie de l'utilisateur est spécifique au compte Windows sur lequel le service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] s'exécute.  
  
-   Stratégie de l'hôte : il s'agit de la stratégie configurée par l'hôte du CLR (dans ce cas, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) qui est appliquée pour le code managé qui s'exécute sur cet hôte.  
  
 Le mécanisme de sécurité d'accès du code pris en charge par le CLR est basé sur la supposition que le module d'exécution peut héberger à la fois du code d'un niveau de confiance total et d'un niveau de confiance partiel. Les ressources protégées par la sécurité d'accès du code CLR sont généralement intégrées à des interfaces de programmation d'applications managées qui requièrent l'autorisation correspondante avant d'accorder l'accès à la ressource. La demande d'autorisation est satisfaite seulement si tous les appelants (au niveau de l'assembly) de la pile d'appels ont l'autorisation pour la ressource correspondante.  
  
 Le jeu d'autorisations de sécurité d'accès du code accordées au code managé en cas d'exécution à l'intérieur de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est l'intersection du jeu d'autorisations accordées par les trois niveaux de stratégie précités. Même si [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] accorde un jeu d'autorisations à un assembly chargé dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], le jeu éventuel d'autorisations accordées au code utilisateur peut être restreint davantage par les stratégies de l'utilisateur et de l'ordinateur.  
  
## <a name="sql-server-host-policy-level-permission-sets"></a>Jeux d'autorisations au niveau stratégie de l'hôte de SQL Server  
 Le jeu d'autorisations de sécurité d'accès du code accordées aux assemblys par le niveau de stratégie de l'hôte [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est déterminé par le jeu d'autorisations spécifié lors de la création de l'assembly. Il existe trois jeux d’autorisations : **Safe**, **EXTERNAL_ACCESS** et **unsafe** (spécifié à l’aide de l’option **PERMISSION_SET** de [Create Assembly &#40;Transact-SQL&#41;](../../../t-sql/statements/create-assembly-transact-sql.md)).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournit un niveau de stratégie de sécurité au niveau de l'hôte au CLR (Common Language Runtime) quand il l'héberge ; cette stratégie est un niveau de stratégie supplémentaire sous les deux niveaux de stratégie qui sont toujours effectifs. Cette stratégie est définie pour chaque domaine d'application qui est créé par [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Cette stratégie n'est pas destinée au domaine d'application par défaut appliqué lorsque [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] crée une instance du CLR.  
  
 La stratégie de niveau hôte de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est une combinaison de la stratégie fixe de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour les assemblys système et de la stratégie spécifiée par l’utilisateur pour les assemblys utilisateur.  
  
 La stratégie fixe pour les assemblys CLR et les assemblys système [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] leur accorde une confiance totale.  
  
 La partie spécifiée par l'utilisateur de la stratégie de l'hôte [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est basée sur le propriétaire de l'assembly spécifiant un des trois compartiments d'autorisation pour chaque assembly. Pour plus d'informations sur les autorisations de sécurité répertoriées ci-dessous, consultez le kit de développement logiciel SDK .NET Framework.  
  
### <a name="safe"></a>SAFE  
 Seul le calcul interne et l’accès aux données locales sont autorisés. **Safe** est le jeu d’autorisations le plus restrictif. Le code exécuté par un assembly avec des autorisations **sécurisées** ne peut pas accéder aux ressources système externes telles que les fichiers, le réseau, les variables d’environnement ou le registre.  
  
 Les assemblys **sécurisés** ont les autorisations et valeurs suivantes :  
  
|Autorisation|Valeur(s)/description|  
|----------------|-----------------------------|  
|**Autorisation**|**Exécution :** Autorisation d’exécuter du code managé.|  
|**SqlClientPermission**|**Context connection = true**, **contexte Connection = Yes**: seule la connexion Context peut être utilisée et la chaîne de connexion ne peut spécifier que la valeur « context connection = true » ou « context connection = Yes ».<br /><br /> **AllowBlankPassword = false :**  Les mots de passe vides ne sont pas autorisés.|  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 Les assemblys EXTERNAL_ACCESS ont les mêmes autorisations que les assemblys **sécurisés** , avec la capacité supplémentaire d’accéder aux ressources système externes telles que les fichiers, les réseaux, les variables d’environnement et le registre.  
  
 **EXTERNAL_ACCESS** assemblys possèdent également les autorisations et les valeurs suivantes :  
  
|Autorisation|Valeur(s)/description|  
|----------------|-----------------------------|  
|**DistributedTransactionPermission**|Non **restreint :** Les transactions distribuées sont autorisées.|  
|**DNSPermission**|Non **restreint :** Autorisation de demander des informations à partir de serveurs de noms de domaine.|  
|**Autorisation**|Non **restreint :** L’accès complet aux variables d’environnement système et utilisateur est autorisé.|  
|**EventLogPermission**|**Administrer :** Les actions suivantes sont autorisées : créer une source d’événements, lire des journaux existants, supprimer des sources ou des journaux d’événements, répondre à des entrées, effacer un journal des événements, écouter des événements et accéder à une collection de tous les journaux des événements.|  
|**FileIOPermission**|Non **restreint :** L’accès complet aux fichiers et aux dossiers est autorisé.|  
|**KeyContainerPermission**|Non **restreint :** L’accès complet aux conteneurs de clés est autorisé.|  
|**NetworkInformationPermission**|**Accès :** Le test ping est autorisé.|  
|**Autorisation**|Autorise les droits de lecture sur **HKEY_CLASSES_ROOT**, **HKEY_LOCAL_MACHINE**, **HKEY_CURRENT_USER**, **HKEY_CURRENT_CONFIG**et **HKEY_USERS.**|  
|**Autorisation**|**Assertion :** Possibilité d’affirmer que tous les appelants de ce code ont l’autorisation requise pour l’opération.<br /><br /> **ControlPrincipal :** Possibilité de manipuler l’objet principal.<br /><br /> **Exécution :** Autorisation d’exécuter du code managé.<br /><br /> **SerializationFormatter :** Possibilité de fournir des services de sérialisation.|  
|**SmtpPermission**|**Accès :** Les connexions sortantes vers le port d’hôte SMTP 25 sont autorisées.|  
|**SocketPermission**|**Se connecter :** Les connexions sortantes (tous les ports, tous les protocoles) sur une adresse de transport sont autorisées.|  
|**SqlClientPermission**|Non **restreint :** L’accès complet à la source de source est autorisé.|  
|**StorePermission**|Non **restreint :** L’accès complet aux magasins de certificats X. 509 est autorisé.|  
|**WebPermission**|**Se connecter :** Les connexions sortantes aux ressources Web sont autorisées.|  
  
### <a name="unsafe"></a>UNSAFE  
 UNSAFE offre aux assemblies un accès sans restriction aux ressources, à la fois à l'intérieur et à l'extérieur de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le code qui s’exécute à partir d’un assembly **non sécurisé** peut également appeler du code non managé.  
  
 Les assemblys **non sécurisés** reçoivent **FullTrust**.  
  
> [!IMPORTANT]  
>  **Safe** est le paramètre d’autorisation recommandé pour les assemblys qui effectuent des tâches de calcul et de gestion des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]données sans accéder aux ressources en dehors de. **EXTERNAL_ACCESS** est recommandé pour les assemblys qui accèdent à des ressources en dehors [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]de. **EXTERNAL_ACCESS** assemblys par défaut s’exécutent [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en tant que compte de service. Il est possible pour **EXTERNAL_ACCESS** code d’emprunter explicitement l’identité du contexte de sécurité de l’authentification Windows de l’appelant. Étant donné que la valeur par défaut consiste [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] à s’exécuter en tant que compte de service, l’autorisation d’exécuter **EXTERNAL_ACCESS** doit être accordée uniquement aux connexions approuvées pour s’exécuter en tant que compte de service. Du point de vue de la sécurité, les **EXTERNAL_ACCESS** et les assemblys **non sécurisés** sont identiques. Toutefois, les assemblys **EXTERNAL_ACCESS** fournissent diverses protections de fiabilité et de robustesse qui ne sont pas dans les ASSEMBLYS non **sécurisés** . Le fait de spécifier **unsafe** permet au code de l’assembly d’effectuer [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] des opérations illégales sur l’espace de processus et peut donc compromettre la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]robustesse et l’extensibilité de. Pour plus d’informations sur la création d' [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]assemblys CLR dans, consultez [gestion des assemblys d’intégration du CLR](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md).  
  
## <a name="accessing-external-resources"></a>Accès aux ressources externes  
 Si un type défini par l’utilisateur (UDT), une procédure stockée ou un autre type d’assembly de construction est inscrit avec le jeu d’autorisations **Safe** , le code managé qui s’exécute dans la construction ne peut pas accéder aux ressources externes. Toutefois, si les jeux d’autorisations **EXTERNAL_ACCESS** ou **unsafe** sont spécifiés et que le code managé tente d’accéder aux [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ressources externes, applique les règles suivantes :  
  
|Si|Alors|  
|--------|----------|  
|Le contexte d'exécution correspond à une connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|Les tentatives d'accéder aux ressources externes sont refusées et une exception de sécurité est levée.|  
|Le contexte d'exécution correspond à une connexion Windows et le contexte d'exécution est l'appelant d'origine.|La ressource externe est accédée sous le contexte de sécurité du compte de service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|L'appelant n'est pas l'appelant d'origine.|L'accès est refusé et une exception de sécurité est levée.|  
|Le contexte d’exécution correspond à une connexion Windows et le contexte d’exécution est l’appelant d’origine et l’appelant a été représenté.|L'accès s'effectue en utilisant le contexte de sécurité de l'appelant, et non le compte de service.|  
  
## <a name="permission-set-summary"></a>Synthèse des jeux d'autorisations  
 Le graphique suivant résume les restrictions et les autorisations accordées aux jeux d’autorisations **Safe**, **EXTERNAL_ACCESS**et **unsafe** .  
  
|||||  
|-|-|-|-|  
||**SAFE**|**EXTERNAL_ACCESS**|**UNSAFE**|  
|**Autorisations de sécurité d’accès du code**|Exécution uniquement|Exécution + accès aux ressources externes|Illimité (y compris P/Invoke)|  
|**Restrictions du modèle de programmation**|Oui|Oui|Aucune restriction|  
|**Vérifiabilité requise**|Oui|Oui|Non|  
|**Accès aux données locales**|Oui|Oui|Oui|  
|**Possibilité d'appeler du code natif**|Non|Non|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité de l’intégration du CLR](../../../relational-databases/clr-integration/security/clr-integration-security.md)   
 [Attributs de protection de l’hôte et programmation de l’intégration du CLR](../../../relational-databases/clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Restrictions du modèle de programmation de l’intégration du CLR](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Environnement hébergé CLR](../../../relational-databases/clr-integration/clr-integration-architecture-clr-hosted-environment.md)  
  
  
