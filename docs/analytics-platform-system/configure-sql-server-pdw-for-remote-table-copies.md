---
title: Configurer SQL Server PDW pour les Copies de la Table distante (SQL Server PDW)
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: 
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 496b4214-5891-404c-8237-c2a1e09db6d5
caps.latest.revision: "11"
ms.openlocfilehash: 08257e4823eed7bf86977ddca1df41eee7f8bda2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="configure-sql-server-pdw-for-remote-table-copies"></a>Configurer SQL Server PDW pour les Copies de la Table distante
Décrit comment configurer SQL Server PDW pour utiliser la fonctionnalité de copie de table distante pour copier des tables aux bases de données SMP SQL Server sur des serveurs non-appliance.  
  
Cette rubrique décrit l’une des étapes de configuration pour la configuration de copie de la table distante. Pour obtenir la liste de toutes les étapes de configuration, consultez [copie distante de la Table](remote-table-copy.md).  
  
## <a name="before-you-begin"></a>Avant de commencer  
Pour configurer SQL Server PDW pour utiliser la copie de la table distante, vous devez :  
  
-   Disposer d’un compte d’administrateur système de plateforme Analytique avec la possibilité de se connecter directement à la  ***appliance_domain*-AD01** et  ***appliance_domain*-AD02** nœuds.  
  
-   Connaître le nom d’hôte ou nom IP du serveur de destination.  
  
## <a name="HowToPDW"></a>Configurer SQL Server PDW pour la copie de la Table distante : mettre à jour les noms d’hôte dans DNS  
Le **CREATE REMOTE TABLE** instruction, utilisée pour les copies de la table distante, spécifie le serveur de destination à l’aide de l’adresse IP ou le nom de l’IP du système SMP Windows. Pour utiliser le nom IP, vous devez ajouter des entrées pour une résolution correcte des noms pour le serveur DNS.  
  
Les étapes suivantes expliquent comment mettre à jour le serveur DNS.  
  
1.  Ouvrez une session sur le nœud actif AD (normalement  ***appliance_domain*-AD01**).  
  
2.  Ouvrez le Gestionnaire DNS. Celui-ci se trouve sous **outils d’administration** dans les **Démarrer** menu.  
  
3.  Utilisez le Gestionnaire DNS pour ajouter le nom IP.  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[Un redirecteur DNS permet de résoudre les noms DNS de l’autre que l’Appliance](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
<!-- MISSING LINKS 
[Security - Configure Domain Trusts &#40;SQL Server PDW&#41;](../sqlpdw/security-configure-domain-trusts-sql-server-pdw.md)  
-->
  
