---
title: Bonnes pratiques pour Data Migration Assistant
description: Apprenez les meilleures pratiques pour la migration des bases de données SQL Server avec Data Migration Assistant
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
author: HJToland3
ms.author: rajpo
ms.openlocfilehash: f2bfbb79a8a4803bb56e3dce85f575e8cf257b4a
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388153"
---
# <a name="best-practices-for-running-data-migration-assistant"></a>Meilleures pratiques pour l’exécution de l’assistant Migration de données
Cet article fournit quelques informations sur les meilleures pratiques pour l’installation, l’évaluation et la migration.

## <a name="installation"></a>Installation
N’installez pas et n’exécutez pas l’assistant de migration de données directement sur la machine d’hôte SQL Server.

## <a name="assessment"></a>Évaluation
- Exécuter des évaluations sur les bases de données de production pendant les périodes de pointe.
- Effectuer les **questions de compatibilité** et **les nouvelles évaluations des recommandations** de fonctionnalités séparément pour réduire la durée de l’évaluation.

## <a name="migration"></a>Migration
- Migrez un serveur pendant les heures de pointe.

- Lorsque vous migrez une base de données, fournissez une localisation d’action unique accessible par le serveur source et le serveur cible, et évitez une opération de copie si possible. Une opération de copie peut introduire un retard en fonction de la taille du fichier de sauvegarde. L’opération de copie augmente également les chances qu’une migration échoue en raison d’une étape supplémentaire. Lorsqu’un seul emplacement est fourni, Data Migration Assistant contourne l’opération de copie.
 
    En outre, assurez-vous que de fournir les autorisations correctes au dossier partagé pour éviter les défaillances de migration. Les autorisations correctes sont spécifiées dans l’outil. Si une instance SQL Server s’exécute sous les informations d’identification du service réseau, donnez les autorisations correctes sur le dossier partagé au compte de la machine pour l’instance SQL Server.

- Activez la connexion de chiffrement lors de la connexion aux serveurs source et cible. L’utilisation du chiffrement TLS augmente la sécurité des données transmises sur les réseaux entre Data Migration Assistant et l’instance SQL Server, ce qui est bénéfique en particulier lors de la migration des connexions SQL. Si le chiffrement TLS n’est pas utilisé et que le réseau est compromis par un attaquant, les connexions SQL migrées pourraient être interceptées et/ou modifiées à la volée par l’attaquant.

    Toutefois, si tous les accès impliquent une configuration intranet sécurisée, le chiffrement peut s'avérer superflu. L’activation du chiffrement ralentit les performances parce que les frais généraux supplémentaires sont nécessaires pour chiffrer et déchiffrer les paquets. Pour plus d’informations, veuillez consulter [le site de cryptage des connexions vers SQL Server](https://go.microsoft.com/fwlink/?linkid=832513).
    
- Vérifiez les contraintes non fiables tant sur la base de données source que sur la base de données cible avant de migrer les données. Après la migration, analysez à nouveau la base de données cible pour voir si des contraintes ne sont pas fiables dans le cadre du mouvement des données. Fixez les contraintes non fiables au besoin. Laisser les contraintes non fiables peut entraîner de mauvais plans d’exécution, et cela peut affecter les performances.
