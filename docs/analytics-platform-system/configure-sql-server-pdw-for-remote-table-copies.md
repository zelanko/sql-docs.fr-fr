---
title: Copies de tables distantes
description: Décrit comment configurer des Data Warehouse parallèles pour utiliser la fonctionnalité de copie de table distante pour copier des tables vers des bases de données SMP SQL Server sur des serveurs non-appliance.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 6c9a0a29b543eb287c7e233d6b1ea77bb2a0d45c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "74401263"
---
# <a name="configure-parallel-data-warehouse-for-remote-table-copies"></a>Configurer des Data Warehouse parallèles pour les copies de tables distantes
Décrit comment configurer SQL Server PDW pour utiliser la fonctionnalité de copie de table distante pour copier des tables vers des bases de données SMP SQL Server sur des serveurs non-appliance.  
  
Cette rubrique décrit l’une des étapes de configuration de la configuration de la copie des tables distantes. Pour obtenir la liste de toutes les étapes de configuration, consultez [copie de table distante](remote-table-copy.md).  
  
## <a name="before-you-begin"></a>Avant de commencer  
Pour configurer SQL Server PDW pour utiliser la copie de table distante, vous devez :  
  
-   Disposer d’un compte d’administrateur système de plateforme d’analyse avec la possibilité de se connecter directement aux nœuds <strong> *appliance_domain*-ad01</strong> et <strong> *appliance_domain*-AD02</strong> .  
  
-   Connaissez le nom d’hôte ou le nom IP du serveur de destination.  
  
## <a name="configure-sql-server-pdw-for-remote-table-copy-update-host-names-in-dns"></a><a name="HowToPDW"></a>Configurer SQL Server PDW pour la copie de table distante : mettre à jour les noms d’hôte dans DNS  
L’instruction **Create Remote table** , utilisée pour les copies de tables distantes, spécifie le serveur de destination à l’aide de l’adresse IP ou du nom d’adresse IP du système Windows SMP. Pour utiliser le nom IP, vous devez ajouter des entrées pour la résolution de noms réussie au serveur DNS.  
  
Les étapes suivantes décrivent comment mettre à jour le serveur DNS.  
  
1.  Connectez-vous au nœud Active Directory actif (normalement <strong> *appliance_domain*-ad01</strong>).  
  
2.  Ouvrez le Gestionnaire DNS. Il se trouve sous **Outils d’administration** dans le menu **Démarrer** .  
  
3.  Utilisez le Gestionnaire DNS pour ajouter le nom d’adresse IP.  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[Utiliser un redirecteur DNS pour résoudre les noms DNS non-Appliance](use-a-dns-forwarder-to-resolve-non-appliance-dns-names.md)  
<!-- MISSING LINKS 
[Security - Configure Domain Trusts &#40;SQL Server PDW&#41;](../sqlpdw/security-configure-domain-trusts-sql-server-pdw.md)  
-->
  
