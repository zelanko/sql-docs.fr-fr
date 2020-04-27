---
title: Sécurité d’accès du code d’intégration du CLR | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
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
manager: craigg
ms.openlocfilehash: d829ef131bc8772ce2d84391513ffa52b2f2ff1a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62873741"
---
# <a name="clr-integration-code-access-security"></a>Sécurité d'accès du code de l'intégration du CLR
  Le common language runtime (CLR) prend en charge un modèle de sécurité appelé sécurité d’accès du code pour le code managé. Dans ce modèle, les autorisations sont accordées aux assemblys selon l'identité du code. Pour plus d'informations, consultez la section relative à la sécurité d'accès du code dans le kit de développement logiciel (SDK) .NET Framework.  
  
 La stratégie de sécurité qui détermine les autorisations accordée aux assemblys est définie dans trois emplacements différents :  
  
-   Stratégie de l'ordinateur : il s'agit de la stratégie appliquée pour tout le code managé qui s'exécute sur l'ordinateur sur lequel [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est installé.  
  
-   Stratégie de l'utilisateur : il s'agit de la stratégie appliquée pour le code managé hébergé par un processus. Pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] le service est en cours d’exécution.  
  
-   Stratégie de l'hôte : il s'agit de la stratégie configurée par l'hôte du CLR (dans ce cas, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) qui est appliquée pour le code managé qui s'exécute sur cet hôte.  
  
 Le mécanisme de sécurité d'accès du code pris en charge par le CLR est basé sur la supposition que le module d'exécution peut héberger à la fois du code d'un niveau de confiance total et d'un niveau de confiance partiel. Les ressources protégées par la sécurité d’accès du code CLR sont généralement encapsulées par les interfaces de programmation d’applications managées qui requirethe l’autorisation correspondante avant d’autoriser l’accès à la ressource. Demandfor l’autorisation est satisfaite uniquement si tous les appelants (au niveau de l’assembly) dans la pile des appels ont l’autorisation de ressource correspondante.  
  
 L’ensemble des autorisations de sécurité d’accès du code qui sont accordées au code [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] managé lors de l’exécution de dans octroie un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]jeu d’autorisations à un assembly chargé dans, le jeu d’autorisations éventuellement accordé au code utilisateur peut être restreint davantage par les stratégies de l’utilisateur et de l’ordinateur.  
  
## <a name="sql-server-host-policy-level-permission-sets"></a>Jeux d'autorisations au niveau stratégie de l'hôte de SQL Server  
 Le jeu d'autorisations de sécurité d'accès du code accordées aux assemblys par le niveau de stratégie de l'hôte [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est déterminé par le jeu d'autorisations spécifié lors de la création de l'assembly. Il existe trois jeux d’autorisations `SAFE`: `EXTERNAL_ACCESS` , `UNSAFE` et (spécifiés à l’aide de l’option **PERMISSION_SET** de[Create Assembly &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-assembly-transact-sql)).  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Cette stratégie n'est pas destinée au domaine d'application par défaut appliqué lorsque [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] crée une instance du CLR.  
  
 Fixedpolicy [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour les assemblys système et la stratégie spécifiée par l’utilisateur pour les assemblys utilisateur.  
  
 La stratégie fixe pour les assemblys CLR et les assemblys système [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] leur accorde une confiance totale.  
  
 La partie spécifiée par l'utilisateur de la stratégie de l'hôte [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est basée sur le propriétaire de l'assembly spécifiant un des trois compartiments d'autorisation pour chaque assembly. Pour plus d'informations sur les autorisations de sécurité répertoriées ci-dessous, consultez le kit de développement logiciel SDK .NET Framework.  
  
### <a name="safe"></a>SAFE  
 Seul le calcul interne et l’accès aux données locales sont autorisés. `SAFE` est le jeu d'autorisations le plus restrictif. Le code exécuté par un assembly à l'aide des autorisations `SAFE` ne peut pas accéder aux ressources système externes telles que les fichiers, le réseau, les variables d'environnement ou le Registre.  
  
 Les assemblys `SAFE` ont les autorisations et valeurs suivantes :  
  
|Autorisation|Valeur(s)/description|  
|----------------|-----------------------------|  
|`SecurityPermission`|`Execution:` autorisation d'exécuter le code managé.|  
|`SqlClientPermission`|`Context connection = true`, `context connection = yes`: seule la connexion contextuelle peut être utilisée et la chaîne de connexion peut spécifier uniquement une valeur de « context connection=true » ou « context connection=yes ».<br /><br /> **AllowBlankPassword = false :**  Les mots de passe vides ne sont pas autorisés.|  
  
### <a name="external_access"></a>EXTERNAL_ACCESS  
 Les assemblys EXTERNAL_ACCESS ont les mêmes autorisations `SAFE` que les assemblys, avec la capacité supplémentaire d’accéder aux ressources système externes telles que les fichiers, les réseaux, les variables d’environnement et le registre.  
  
 Les assemblys `EXTERNAL_ACCESS` ont également les autorisations et valeurs suivantes :  
  
|Autorisation|Valeur(s)/description|  
|----------------|-----------------------------|  
|`DistributedTransactionPermission`|`Unrestricted:`Les transactions distribuées sont autorisées.|  
|`DNSPermission`|`Unrestricted:`Autorisation de demander des informations à partir de serveurs de noms de domaine.|  
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
>  `SAFE` est le paramètre recommandé pour les autorisations des assemblys qui effectuent des calculs et des tâches de gestion des données sans accéder à des ressources extérieures à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. `EXTERNAL_ACCESS`par défaut, les assemblys s' [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] exécutent en tant que compte `EXTERNAL_ACCESS` de service, l’autorisation d’exécuter ne doit être accordée qu’aux connexions approuvées pour s’exécuter en tant que compte de service. Du point de vue de la sécurité, les assemblys `EXTERNAL_ACCESS` et `UNSAFE` sont identiques. Toutefois, les assemblys `EXTERNAL_ACCESS` fournissent différentes protections en matière de fiabilité et de robustesse absentes des assemblys `UNSAFE`. La `UNSAFE` spécification de permet au code de l’assembly d’effectuer des [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]opérations illégales sur le. Pour plus d’informations sur la création d' [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]assemblys CLR dans, consultez [gestion des assemblys d’intégration du CLR](../../../relational-databases/clr-integration/assemblies/managing-clr-integration-assemblies.md).  
  
## <a name="accessing-external-resources"></a>Accès aux ressources externes  
 Si un type défini par l'utilisateur (UDT), une procédure stockée ou autre type d'assembly de construction est inscrit avec le jeu d'autorisations `SAFE`, le code managé qui s'exécute dans la construction ne peut pas accéder aux ressources externes. Toutefois, si le jeu d'autorisations `EXTERNAL_ACCESS` ou `UNSAFE` est spécifié et que le code managé tente d'accéder aux ressources externes, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] applique les règles suivantes :  
  
|Si|Alors|  
|--------|----------|  
|Le contexte d'exécution correspond à une connexion [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|Les tentatives d'accéder aux ressources externes sont refusées et une exception de sécurité est levée.|  
|Le contexte d'exécution correspond à une connexion Windows et le contexte d'exécution est l'appelant d'origine.|La ressource externe est accédée sous le contexte de sécurité du compte de service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|L'appelant n'est pas l'appelant d'origine.|L'accès est refusé et une exception de sécurité est levée.|  
|Le contexte d’exécution correspond à une connexion Windows et le contexte d’exécution est l’appelant d’origine et l’appelant a été représenté.|L'accès s'effectue en utilisant le contexte de sécurité de l'appelant, et non le compte de service.|  
  
## <a name="permission-set-summary"></a>Synthèse des jeux d'autorisations  
 Le graphique suivant résume les restrictions et autorisations accordées aux jeux d'autorisations `SAFE`, `EXTERNAL_ACCESS` et `UNSAFE`.  
  
|||||  
|-|-|-|-|  
||`SAFE`|`EXTERNAL_ACCESS`|`UNSAFE`|  
|`Code Access Security Permissions`|Exécution uniquement|Exécution + accès aux ressources externes|Illimité (y compris P/Invoke)|  
|`Programming model restrictions`|Oui|Oui|Aucune restriction|  
|`Verifiability requirement`|Oui|Oui|Non|  
|`Local data access`|Oui|Oui|Oui|  
|`Ability to call native code`|Non|Non|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité de l’intégration du CLR](clr-integration-security.md)   
 [Attributs de protection de l’hôte et programmation de l’intégration du CLR](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [Restrictions du modèle de programmation de l’intégration du CLR](../../../relational-databases/clr-integration/database-objects/clr-integration-programming-model-restrictions.md)   
 [Environnement hébergé CLR](../clr-integration-architecture-clr-hosted-environment.md)  
  
  
