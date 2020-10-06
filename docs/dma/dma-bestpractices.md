---
title: Bonnes pratiques pour Data Migration Assistant
description: Découvrez les meilleures pratiques pour la migration de bases de données SQL Server avec Assistant Migration de données, y compris des informations sur l’installation, l’évaluation et la migration.
ms.custom: seo-lt-2019
ms.date: 03/12/2019
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.technology: dma
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Best Practices
ms.assetid: ''
author: rajeshsetlem
ms.author: rajpo
ms.openlocfilehash: 440d6d12ed639d158ad0309209b60daa56e08322
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727780"
---
# <a name="best-practices-for-running-data-migration-assistant"></a>Bonnes pratiques pour l’exécution de l’Assistant Migration de données
Cet article fournit des informations sur les meilleures pratiques pour l’installation, l’évaluation et la migration.

## <a name="installation"></a>Installation
N’installez pas et n’exécutez pas le Assistant Migration de données directement sur l’ordinateur hôte SQL Server.

## <a name="assessment"></a>Évaluation
- Exécuter des évaluations sur les bases de données de production pendant les heures creuses.
- Pour réduire la durée de l’évaluation, vous pouvez effectuer des analyses de **compatibilité** et de **nouvelles recommandations** sur les fonctionnalités séparément.

## <a name="migration"></a>Migration
- Migrez un serveur en dehors des heures de pointe.

- Lors de la migration d’une base de données, fournissez un emplacement de partage unique accessible par le serveur source et le serveur cible, et évitez une opération de copie si possible. Une opération de copie peut introduire un délai en fonction de la taille du fichier de sauvegarde. L’opération de copie augmente également les risques d’échec d’une migration en raison d’une étape supplémentaire. Lorsqu’un emplacement unique est fourni, Assistant Migration de données ignore l’opération de copie.
 
    En outre, assurez-vous que pour fournir les autorisations appropriées au dossier partagé afin d’éviter les échecs de migration. Les autorisations appropriées sont spécifiées dans l’outil. Si une instance de SQL Server s’exécute sous informations d’identification de service réseau, attribuez les autorisations appropriées sur le dossier partagé au compte d’ordinateur pour l’instance de SQL Server.

- Activez le chiffrement de la connexion lors de la connexion aux serveurs source et cible. L’utilisation du chiffrement TLS augmente la sécurité des données transmises sur les réseaux entre Assistant Migration de données et l’instance de SQL Server, ce qui est particulièrement utile lors de la migration de connexions SQL. Si le chiffrement TLS n’est pas utilisé et que le réseau est compromis par une personne malveillante, les connexions SQL en cours de migration peuvent être interceptées et/ou modifiées à la volée par l’attaquant.

    Toutefois, si tous les accès impliquent une configuration intranet sécurisée, le chiffrement peut s'avérer superflu. L’activation du chiffrement ralentit les performances, car la surcharge supplémentaire requise pour chiffrer et déchiffrer les paquets. Pour plus d’informations, consultez [chiffrement des connexions à SQL Server](/previous-versions/sql/sql-server-2008-r2/ms189067(v=sql.105)).
    
- Vérifiez les contraintes non fiables sur la base de données source et la base de données cible avant de migrer les données. Après la migration, analysez de nouveau la base de données cible pour voir si des contraintes n’ont pas été approuvées dans le cadre du déplacement des données. Corrigez les contraintes non fiables en fonction des besoins. Si vous laissez les contraintes non approuvées, vous risquez d’obtenir des plans d’exécution médiocres, et cela peut affecter les performances.