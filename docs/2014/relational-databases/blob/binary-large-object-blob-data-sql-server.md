---
title: Données blob (Binary Large Object) (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], design and implementation
ms.assetid: 97509274-c3f8-43e5-a37c-52f1ffe0961a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a663dedf34d75a21ee8df6b97979548c04abf7ff
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84955799"
---
# <a name="binary-large-object-blob-data-sql-server"></a>Données blob (Binary Large Object) (SQL Server)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des solutions pour stocker des fichiers et des documents dans la base de données ou sur des dispositifs de stockage distants.  
  
##  <a name="in-this-section"></a><a name="section"></a> Dans cette section  
 [Comparer les options pour le stockage des objets blob &#40;SQL Server&#41;](compare-options-for-storing-blobs-sql-server.md)  
 Comparez les avantages de FILESTREAM, de FileTables et de magasin d'objets BLOB distants (RBS).  
  
 [FILESTREAM &#40;SQL Server&#41;](filestream-sql-server.md)  
 FILESTREAM permet aux applications [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de stocker des données non structurées, telles que des documents et des images, dans le système de fichiers. Les applications peuvent tirer parti des API de diffusion et des performances du système de fichiers, et en même temps maintenir la cohérence transactionnelle entre les données non structurées et les données structurées correspondantes.  
  
 [FileTables &#40;SQL Server&#41;](filetables-sql-server.md)  
 La fonctionnalité FileTable apporte une prise en charge de l'espace de noms de fichier Windows et la compatibilité des applications Windows avec les données de fichier stockées dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. FileTable permet à une application d'intégrer ses composants de stockage et de gestion des données, et fournit des services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] intégrés (notamment la recherche sémantique et en texte intégral) sur des données et des métadonnées non structurées.  
  
 En d'autres termes, vous pouvez maintenant stocker des fichiers et des documents dans des tables spéciales dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , appelées FileTables, mais y accéder à partir d'applications Windows comme si ils avaient été stockés dans le système de fichiers, sans apporter de modifications à vos applications clientes.  
  
 [Magasin d’objets blob distants &#40;RBS&#41; &#40;SQL Server&#41;](remote-blob-store-rbs-sql-server.md)  
 Le magasin d'objets blob distants (RBS) pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permet aux administrateurs de base de données de stocker des objets blob (Binary Large Object) dans des solutions de stockage de marchandises et non pas directement sur le serveur. Cela permet d'économiser une grande quantité d'espace et d'éviter le gaspillage des précieuses ressources matérielles du serveur. RBS fournit un ensemble de bibliothèques API qui définissent un modèle standardisé d'accès aux données BLOB pour les applications. RBS comprend également des outils de maintenance, tels que le nettoyage de la mémoire, permettant de gérer les données BLOB distantes.  
  
 RBS est inclus dans le CD d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , mais n'est pas installé par le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
  
