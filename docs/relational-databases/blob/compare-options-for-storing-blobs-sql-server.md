---
title: Comparer les options pour le stockage des objets blob (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
ms.assetid: 6038697b-36a9-49e8-a02a-2ad9e2e60e5a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 68efb09a2b6d2a3ace441107ed9160fede154c8a
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68085442"
---
# <a name="compare-options-for-storing-blobs-sql-server"></a>Comparer les options pour le stockage des objets blob (SQL Server)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Explique et compare les options disponibles pour stocker des fichiers et des documents dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

## <a name="Expectations"></a> Stockage de fichiers dans la base de données - Avantages et attentes

Un pourcentage important des données d'entreprise correspond à des données non structurées par nature et est stocké en général sous la forme de fichiers et de documents dans des systèmes de fichiers. La plupart de ces données sont produites, gérées et consommées par des applications qui accèdent aux fichiers via des API Windows. Les entreprises conservent en général ces données dans le système de fichiers, en stockant les métadonnées connexes des fichiers dans une base de données relationnelle.

L’intégration de données non structurées dans la base de données relationnelle offre les avantages suivants :

- Fonctions intégrées de stockage et de gestion des données telles que la sauvegarde.
- Services intégrés tels que la recherche en texte intégral et la recherche sémantique sur les données et métadonnées.
- Facilité d'administration et gestion de la stratégie sur les données non structurées.

D’une façon générale, il a été peu pratique de stocker des données non structurées dans une base de données relationnelle. Réécrire des applications établies (comme Microsoft Word ou Adobe Reader) pour interagir via des API de base de données relationnelle s’est révélé impraticable. Ces applications attendent que les données soient accessibles via des API Windows. Les applications ont les attentes suivantes :

- Les applications Windows ne sont pas informées des transactions de base de données et ne les requièrent pas.
- Les applications Windows requièrent la compatibilité avec les API du système de fichiers pour les données de répertoire et de fichier.

Il y a plusieurs années, SQL Server n’offrait aucun moyen de stocker des données non structurées dans une base de données relationnelle. Aujourd’hui cependant, il offre différents moyens de stocker des données non structurées.

## <a name="Filestream"></a> FILESTREAM

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a déjà la fonctionnalité FILESTREAM. La fonctionnalité FILESTREAM fournit un stockage efficace, la gestion et le streaming de données non structurées stockées en tant que fichiers sur le système de fichiers. Toutefois, une solution FILESTREAM nécessite une programmation personnalisée et ne répond pas à la configuration requise en matière de compatibilité complète avec les applications Windows décrite ci-dessus.

## <a name="FileTables"></a> FileTables

La fonctionnalité FileTable s’appuie sur les fonctionnalités existantes de FILESTREAM. La fonctionnalité FileTable permet aux entreprises clientes de stocker les données de fichiers non structurés et des hiérarchies de répertoires dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La fonctionnalité répond à l’exigence d’un accès non transactionnel et de la compatibilité des applications Windows pour les données stockées dans des fichiers.

## <a name="CompareFileTable"></a> Comparaison de FILESTREAM et de FileTable

|Fonctionnalité|Serveur de fichiers et solution de base de données|Solution FILESTREAM|Solution FileTable|
|:------|:--------------------------------|:------------------|:-----------------|
|**Histoire unique pour les tâches de gestion**|Non|Oui|**Oui**|
|**Ensemble unique de services**: recherche, création de rapports, interrogation, etc.|Non|Oui|**Oui**|
|**Modèle de sécurité intégré**|Non|Oui|**Oui**|
|**Mises à jour sur place de données FILESTREAM**|Oui|Non|**Oui**|
|**Hiérarchie de répertoires et de fichiers maintenue dans la base de données**|Non|Non|**Oui**|
|**Compatibilité d'applications Windows**|Oui|Non|**Oui**|
|**Accès relationnel aux attributs de fichier**|Non|Non|**Oui**|

## <a name="CompareRBS"></a> Comparaison de FILESTREAM et du magasin d'objets blob distants (RBS)

Une autre option pour stocker des données non structurées implique un magasin d’objets blob distants (RBS). Pour plus d’informations, consultez [Magasin d’objets blob distants (RBS) (SQL Server)](remote-blob-store-rbs-sql-server.md).

## <a name="more"></a> Informations supplémentaires

[FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md)  
[FileTables &#40;SQL Server&#41;](../../relational-databases/blob/filetables-sql-server.md)  
[Magasin d’objets blob distants &#40;RBS&#41; &#40;SQL Server&#41;](../../relational-databases/blob/remote-blob-store-rbs-sql-server.md)
