---
title: Configurer Parallel Data Warehouse pour les copies de la table distante | Microsoft Docs
description: Décrit comment configurer Parallel Data Warehouse pour utiliser la fonctionnalité de copie de table distante pour copier des tables vers les bases de données SQL Server SMP sur les serveurs non-appliance.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: fdac0b6ed211e223c3fad7ba15ac79a282c61303
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54123910"
---
# <a name="configure-parallel-data-warehouse-for-remote-table-copies"></a>Configurer Parallel Data Warehouse pour les copies de la table distante
Décrit comment configurer SQL Server PDW pour utiliser la fonctionnalité de copie de table distante pour copier des tables vers les bases de données SQL Server SMP sur les serveurs non-appliance.  
  
Cette rubrique décrit l’une des étapes de configuration pour la configuration de copie de la table distante. Pour obtenir la liste de toutes les étapes de configuration, consultez [copie distante de la Table](remote-table-copy.md).  
  
## <a name="before-you-begin"></a>Avant de commencer  
Pour configurer SQL Server PDW pour utiliser la copie de la table distante, vous devez :  
  
-   Disposer d’un compte d’administrateur système de plateforme d’Analytique avec la possibilité de se connecter directement à la  <strong>*appliance_domain*-AD01</strong> et  <strong>*appliance_domain*-AD02</strong> nœuds.  
  
-   Connaître le nom d’hôte ou le nom d’adresse IP du serveur de destination.  
  
## <a name="HowToPDW"></a>Configurer SQL Server PDW pour la copie de la Table distante : Mettre à jour les noms d’hôte dans DNS  
Le **CREATE REMOTE TABLE** instruction, utilisée pour les copies de la table distante, spécifie le serveur de destination à l’aide de l’adresse IP ou le nom de l’adresse IP du système Windows de SMP. Pour utiliser le nom de l’adresse IP, vous devez ajouter des entrées pour la résolution de noms réussie vers le serveur DNS.  
  
Les étapes suivantes décrivent comment mettre à jour le serveur DNS.  
  
1.  Ouvrez une session sur le nœud actif AD (normalement  <strong>*appliance_domain*-AD01</strong>).  
  
2.  Ouvrez le Gestionnaire DNS. Celui-ci se trouve sous **outils d’administration** dans le **Démarrer** menu.  
  
3.  Utilisez le Gestionnaire DNS pour ajouter le nom de l’adresse IP.  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[Utiliser un redirecteur DNS pour résoudre les noms DNS de Non-Appliance](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
<!-- MISSING LINKS 
[Security - Configure Domain Trusts &#40;SQL Server PDW&#41;](../sqlpdw/security-configure-domain-trusts-sql-server-pdw.md)  
-->
  
