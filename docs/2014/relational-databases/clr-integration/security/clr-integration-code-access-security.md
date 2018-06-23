---
title: Sécurité d’accès du Code CLR Integration | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- UNSAFE assemblies
- permissions [CLR integration]
- common language runtime [SQL Server], security
- SAFE assemblies
- code access security [CLR integration]
- EXTERNAL_ACCESS assemblies
ms.assetid: 2111cfe0-d5e0-43b1-93c3-e994ac0e9729
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8ccb03b45b27150c00a5620f772afc764dc6ff0c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043625"
---
# <a name="clr-integration-code-access-security"></a>Sécurité d'accès du code de l'intégration du CLR
  Le common language runtime (CLR) prend en charge un modèle de sécurité appelé sécurité d’accès du code pour le code managé. Dans ce modèle, les autorisations sont accordées aux assemblys selon l'identité du code. Pour plus d'informations, consultez la section relative à la sécurité d'accès du code dans le kit de développement logiciel (SDK) .NET Framework.  
  
 La stratégie de sécurité qui détermine les autorisations accordée aux assemblys est définie dans trois emplacements différents :  
  
-   Stratégie de l'ordinateur : il s'agit de la stratégie appliquée pour tout le code managé qui s'exécute sur l'ordinateur sur lequel [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est installé.  
  
-   Stratégie de l'utilisateur : il s'agit de la stratégie appliquée pour le code managé hébergé par un processus. Pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service est en cours d’exécution.  
  
-   Stratégie de l'hôte : il s'agit de la stratégie configurée par l'hôte du CLR (dans ce cas, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) qui est appliquée pour le code managé qui s'exécute sur cet hôte.  
  
 Le mécanisme de sécurité d'accès du code pris en charge par le CLR est basé sur la supposition que le module d'exécution peut héberger à la fois du code d'un niveau de confiance total et d'un niveau de confiance partiel. Les ressources qui sont protégées par la sécurité d’accès du code CLR sont généralement intégrées à une application managée des interfaces de programmation cette autorisation correspondante requirethe avant d’autoriser l’accès à la ressource. Le demandfor l’autorisation est satisfaite uniquement si tous les appelants (au niveau de l’assembly) dans la pile des appels ont l’autorisation de ressource correspondante.  
  
 Le jeu d’autorisations de sécurité d’accès au code qui sont accordées à code managé lors de l’exécution à l’intérieur de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] accorde un jeu d’autorisations à un assembly chargé dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], le jeu éventuel d’autorisations accordées au code utilisateur peut être limité par le l’utilisateur et les stratégies au niveau de l’ordinateur.  
  
## <a name="sql-server-host-policy-level-permission-sets"></a>Jeux d'autorisations au niveau stratégie de l'hôte de SQL Server  
 Le jeu d'autorisations de sécurité d'accès du code accordées aux assemblys par le niveau de stratégie de l'hôte [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est déterminé par le jeu d'autorisations spécifié lors de la création de l'assembly. Il existe trois jeux d’autorisations : `SAFE`, `EXTERNAL_ACCESS` et `UNSAFE` (spécifié à l’aide de la **PERMISSION_SET** option de[CREATE ASSEMBLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)) .  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Cette stratégie n'est pas destinée au domaine d'application par défaut appliqué lorsque [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] crée une instance du CLR.  
  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fixedpolicy pour les assemblys système et spécifié par l’utilisateur de stratégie pour les assemblys utilisateur.  
  
 La stratégie fixe pour les assemblys CLR et les assemblys système [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] leur accorde une confiance totale.  
  
 La partie spécifiée par l'utilisateur de la stratégie de l'hôte [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est basée sur le propriétaire de l'assembly spécifiant un des trois compartiments d'autorisation pour chaque assembly. Pour plus d'informations sur les autorisations de sécurité répertoriées ci-dessous, consultez le kit de développement logiciel SDK .NET Framework.  
  
### <a name="safe"></a>SAFE  
 Seul un calcul interne et accès aux données locales sont autorisées. `SAFE` est le jeu d'autorisations le plus restrictif. Le code exécuté par un assembly à l'aide des autorisations `SAFE` ne peut pas accéder aux ressources système externes telles que les fichiers, le réseau, les variables d'environnement ou le Registre.  
  
 Les assemblys `SAFE` ont les autorisations et valeurs suivantes :  
  
|Autorisation|Valeur(s)/description|  
|----------------|-----------------------------|  
|`SecurityPermission`|`Execution:` autorisation d'exécuter le code managé.|  
|`SqlClientPermission`|`Context connection = true`, `context connection = yes`: seule la connexion contextuelle peut être utilisée et la chaîne de connexion peut spécifier uniquement une valeur de « context connection=true » ou « context connection=yes ».<br /><br /> **AllowBlankPassword = false :** mots de passe vides ne sont pas autorisées.|  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 Assemblys EXTERNAL_ACCESS ont les mêmes autorisations que `SAFE` assemblys, avec possibilité en prime d’accéder aux ressources système externes telles que des fichiers, des réseaux, des variables d’environnement et le Registre.  
  
 Les assemblys `EXTERNAL_ACCESS` ont également les autorisations et valeurs suivantes :  
  
|Autorisation|Valeur(s)/description|  
|----------------|-----------------------------|  
|`DistributedTransactionPermission`|`Unrestricted:` Les transactions distribuées sont autorisées.|  
|`DNSPermission`|`Unrestricted:` Autorisation de demander des informations à partir des serveurs de noms de domaine.|  
|`EnvironmentPermission`|`Unrestricted:` l'accès complet aux variables du système et de l'environnement utilisateur est accordé.|  
|`EventLogPermission`|`Administer:` les actions suivantes sont autorisées : création d'une source d'événement, lecture de journaux existants, suppression de sources d'événements ou de journaux, réponse aux entrées, effacement d'un journal des événements, écoute des événements et accès à une collection de tous les journaux des événements.|  
|`FileIOPermission`|`Unrestricted:` l'accès complet aux fichiers et aux dossiers est accordé.|  
|`KeyContainerPermission`|`Unrestricted:` l'accès complet aux conteneurs de clés est accordé.|  
|`NetworkInformationPermission`|`Access:` l'exécution de requêtes ping est autorisée.|  
|`RegistryPermission`|Autorise des droits de lecture à `HKEY_CLASSES_ROOT`, `HKEY_LOCAL_MACHINE`, `HKEY_CURRENT_USER`, `HKEY_CURRENT_CONFIG` et `HKEY_USERS.`|  
|`SecurityPermission`|`Assertion:` possibilité de déclarer que tous les appelants de ce code ont l'autorisation requise pour l'opération.<br /><br /> `ControlPrincipal:` possibilité de manipuler l'objet principal<br /><br /> `Execution:` autorisation d'exécuter le code managé.<br /><br /> `SerializationFormatter:` possibilité de fournir des services de sérialisation.|  
|**SmtpPermission**|`Access:` les connexions sortantes au port 25 hôte SMTP sont autorisées.|  
|`SocketPermission`|`Connect:` les connexions sortantes (tous les ports, tous les protocoles) sur une adresse de transport sont autorisées.|  
|`SqlClientPermission`|`Unrestricted:` l'accès complet à la source de données est accordé.|  
|`StorePermission`|`Unrestricted:` l'accès complet aux magasins de certificats X.509 est accordé.|  
|`WebPermission`|`Connect:` les connexions sortantes aux ressources Web sont autorisées.|  
  
### <a name="unsafe"></a>UNSAFE  
 UNSAFE offre aux assemblies un accès sans restriction aux ressources, à la fois à l'intérieur et à l'extérieur de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Le code qui s'exécute dans un assembly `UNSAFE` peut également appeler du code non managé.  
  
 Les assemblys `UNSAFE` dispose de l'approbation `FullTrust`.  
  
> [!IMPORTANT]  
>  `SAFE` est le paramètre recommandé pour les autorisations des assemblys qui effectuent des calculs et des tâches de gestion des données sans accéder à des ressources extérieures à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. `EXTERNAL_ACCESS` par défaut, les assemblys sont exécutées en tant que le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] compte de service, l’autorisation d’exécuter `EXTERNAL_ACCESS` ne devrait être donnée qu’aux connexions approuvées pour exécuter en tant que le compte de service. Du point de vue de la sécurité, les assemblys `EXTERNAL_ACCESS` et `UNSAFE` sont identiques. Toutefois, les assemblys `EXTERNAL_ACCESS` fournissent différentes protections en matière de fiabilité et de robustesse absentes des assemblys `UNSAFE`. Spécification de `UNSAFE` permet au code de l’assembly peut effectuer des opérations illégales par rapport à la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour plus d’informations sur la création d’assemblys CLR dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], consultez [la gestion des assemblys d’intégration du CLR](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md).  
  
## <a name="accessing-external-resources"></a>Accès aux ressources externes  
 Si un type défini par l'utilisateur (UDT), une procédure stockée ou autre type d'assembly de construction est inscrit avec le jeu d'autorisations `SAFE`, le code managé qui s'exécute dans la construction ne peut pas accéder aux ressources externes. Toutefois, si le jeu d'autorisations `EXTERNAL_ACCESS` ou `UNSAFE` est spécifié et que le code managé tente d'accéder aux ressources externes, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] applique les règles suivantes :  
  
|Si|Alors|  
|--------|----------|  
|Le contexte d'exécution correspond à une connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|Les tentatives d'accéder aux ressources externes sont refusées et une exception de sécurité est levée.|  
|Le contexte d'exécution correspond à une connexion Windows et le contexte d'exécution est l'appelant d'origine.|La ressource externe est accédée sous le contexte de sécurité du compte de service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|L'appelant n'est pas l'appelant d'origine.|L'accès est refusé et une exception de sécurité est levée.|  
|Le contexte d’exécution correspond à une connexion Windows et le contexte d’exécution est l’appelant d’origine et l’appelant n’a pas été empruntée.|L'accès s'effectue en utilisant le contexte de sécurité de l'appelant, et non le compte de service.|  
  
## <a name="permission-set-summary"></a>Synthèse des jeux d'autorisations  
 Le graphique suivant résume les restrictions et autorisations accordées aux jeux d'autorisations `SAFE`, `EXTERNAL_ACCESS` et `UNSAFE`.  
  
|||||  
|-|-|-|-|  
||`SAFE`|`EXTERNAL_ACCESS`|`UNSAFE`|  
|`Code Access Security Permissions`|Exécution uniquement|Exécution + accès aux ressources externes|Illimité (y compris P/Invoke)|  
|`Programming model restrictions`|Oui|Oui|Aucune restriction|  
|`Verifiability requirement`|Oui|Oui|non|  
|`Local data access`|Oui|Oui|Oui|  
|`Ability to call native code`|non|non|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité d’intégration du CLR](clr-integration-security.md)   
 [Attributs de Protection d’hôte et de la programmation de l’intégration CLR](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Restrictions du modèle de programmation CLR Integration](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Environnement hébergé CLR](../clr-integration-architecture-clr-hosted-environment.md)  
  
  
