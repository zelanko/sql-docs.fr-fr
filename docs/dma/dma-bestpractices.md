---
title: Meilleures pratiques pour l’Assistant de Migration de données (SQL Server) | Documents Microsoft
ms.custom: ''
ms.date: 06/02/2018
ms.prod: sql
ms.prod_service: dma
ms.reviewer: ''
ms.suite: sql
ms.technology: dma
ms.tgt_pltfrm: ''
ms.topic: conceptual
keywords: ''
helpviewer_keywords:
- Data Migration Assistant, Best Practices
ms.assetid: ''
caps.latest.revision: ''
author: HJToland3
ms.author: jtoland
manager: craigg
ms.openlocfilehash: 8a1b184a6a280b328df35ea04a1ab6caf996c7c8
ms.sourcegitcommit: 6fe7b5e8818bd0d94fce693c560d63cc6883d76f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34758109"
---
# <a name="best-practices-for-running-data-migration-assistant"></a>Meilleures pratiques pour l’exécution de l’Assistant Migration de données
Cet article fournit les meilleures informations pratiques suivantes pour l’installation, d’évaluation et de migration.

## <a name="installation"></a>Installation
Ne pas installer et exécuter l’Assistant de Migration de données directement sur l’ordinateur hôte de SQL Server.

## <a name="assessment"></a>Évaluation
- Exécuter les évaluations sur les bases de données de production pendant les heures creuses.
- Effectuer la **des problèmes de compatibilité** et **nouvelles recommandations fonctionnalité** évaluations séparément pour réduire la durée de l’évaluation.

## <a name="migration"></a>Migration
- Migrer un serveur pendant les heures creuses.
- Lorsque vous migrez une base de données, fournir un emplacement de partage unique accessible par le serveur source et le serveur cible et évitez si possible d’une opération de copie. Une opération de copie peut se traduire en fonction de la taille du fichier de sauvegarde. L’opération de copie augmente également le risque qu’une migration échoue en raison d’une étape supplémentaire. Lorsqu’un seul emplacement est fourni, l’Assistant Migration de données ignore l’opération de copie.
 
    En outre, assurez-vous que pour fournir les autorisations correctes pour le dossier partagé pour éviter les échecs de migration. Les autorisations appropriées sont spécifiées dans l’outil. Si une instance de SQL Server s’exécute sous les informations d’identification de Service réseau, donnez les autorisations appropriées sur le dossier partagé pour le compte d’ordinateur pour l’instance de SQL Server.

- Activer chiffrer la connexion lors de la connexion aux serveurs source et cible. L’utilisation de SSL chiffrement augmente la sécurité des données transmises sur les réseaux entre l’Assistant Migration de données et de l’instance de SQL Server, ce qui est utile surtout lorsque vous migrez des connexions SQL. Si le chiffrement SSL n’est pas utilisé et que le réseau est compromis par un intrus, les connexions SQL en cours de migration peuvent intercepter et/ou modifié à la volée par la personne malveillante.

    Toutefois, si tous les accès impliquent une configuration intranet sécurisée, le chiffrement peut s'avérer superflu. L’activation du chiffrement ralentit les performances, car la charge supplémentaire qui est nécessaire pour chiffrer et déchiffrer des paquets. Pour plus d’informations, reportez-vous à [le chiffrement des connexions à SQL Server](https://go.microsoft.com/fwlink/?linkid=832513).
