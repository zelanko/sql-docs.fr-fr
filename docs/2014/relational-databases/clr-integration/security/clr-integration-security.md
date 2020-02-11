---
title: Sécurité de l’intégration du CLR | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- authorization [CLR integration]
- common language runtime [SQL Server], security
- database objects [CLR integration], security
ms.assetid: 05d7a471-c5d5-4730-b903-e4edc8157bb4
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 12ca3fcb00122313c1d1e4aae8b64733be9140c9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62918991"
---
# <a name="clr-integration-security"></a>Sécurité de l'intégration du CLR
  Le modèle de sécurité du [!INCLUDE[ssNoVersion](../../../includes/dnprdnshort-md.md)] Common Language Runtime (CLR) gère et sécurise l’accès entre les différents types d’objets CLR et non CLR qui [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] s’exécutent dans une instruction ou un autre objet CLR en cours d’exécution sur le serveur. Les appels entre objets portent le nom de liens. Les types de vérifications de sécurité effectués sur ces objets dépendent des types de liens impliqués.  
  
 Le modèle de sécurité d'intégration du CLR a les objectifs suivants :  
  
-   Par défaut, l’exécution du code utilisateur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]managé sur. L'exécution d'opérations susceptibles de compromettre la robustesse de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] doit être protégée par des autorisations de haut niveau appropriées.  
  
-   Le code utilisateur managé ne doit pas accéder de façon non autorisée aux données utilisateur ou autre code utilisateur dans la base de données. Le code défini par l'utilisateur doit s'exécuter sous le contexte de sécurité de la session utilisateur qui l'a appelé et avec les privilèges corrects pour ce contexte de sécurité.  
  
-   Il doit y avoir des contrôles pour restreindre le code utilisateur à accéder à toute ressource située à l'extérieur du serveur, de sorte qu'il soit utilisé strictement pour l'accès aux données et le calcul locaux.  
  
-   Le code défini par l'utilisateur ne doit pas être en mesure d'accéder de façon non autorisée aux ressources système du fait de son exécution dans le processus [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]avec le modèle de sécurité basé sur l’accès du code du CLR. Quelques-uns des avantages offerts par cette approche combinée de la sécurité sont discutés dans cette section.  
  
 Le tableau suivant décrit les rubriques de cette section.  
  
 [Sécurité d'accès du code de l'intégration du CLR](clr-integration-code-access-security.md)  
 Discute du modèle de sécurité d'accès du code pour le code managé.  
  
 [Attributs de protection de l'hôte et programmation de l'intégration CLR](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)  
 Fournit des informations à propos des valeurs d'attributs de protection de l'hôte (HPA) interdites dans les assemblys SAFE et EXTERNAL_ACCESS.  
  
 [Liens dans la sécurité d'intégration du CLR](../../../database-engine/dev-guide/links-in-clr-integration-security.md)  
 Décrit comment les segments de code utilisateur peuvent s'appeler dans [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Emprunt d'identité et sécurité de l'intégration du CLR](../../../database-engine/dev-guide/impersonation-and-clr-integration-security.md)  
 Discute la manière dont le code managé accède aux ressources externes à l'aide de l'emprunt d'identité.  
  
 [Autorisation d'appelants partiellement approuvés](../../../database-engine/dev-guide/allowing-partially-trusted-callers.md)  
 Discute des problèmes qui surviennent lorsqu'une méthode managée appelle une méthode dans une classe contenue dans un autre assembly.  
  
 [Domaines d'application et sécurité de l'intégration du CLR](../../../database-engine/dev-guide/application-domains-and-clr-integration-security.md)  
 Décrit la façon dont les assemblys sont chargés dans les domaines d'application.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des assemblys d'intégration du CLR](../assemblies/managing-clr-integration-assemblies.md)  
  
  
