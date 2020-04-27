---
title: Magasin d’objets blob distants (RBS) (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.technology: filestream
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Remote Blob Store (RBS) [SQL Server]
- RBS (Remote Blob Store) [SQL Server]
ms.assetid: 31c947cf-53e9-4ff4-939b-4c1d034ea5b1
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4379e0ff3ca534acd6ae130cbdf0f8acd2b6a81f
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66009848"
---
# <a name="remote-blob-store-rbs-sql-server"></a>Magasin d'objets blob distants (RBS) (SQL Server)
  Le magasin d'objets blob distants[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est un composant additionnel facultatif qui permet aux administrateurs de base de données de stocker des objets blob dans des solutions de stockage de marchandises au lieu de les stocker directement sur le serveur de base de données principal.  
  
 RBS est inclus dans le CD d'installation de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] , mais n'est pas installé par le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 Pour plus d'informations sur le magasin d'objets blob distants, consultez [RBS Resources](#rbsresources) plus loin dans cette rubrique.  
  
## <a name="benefits-of-rbs"></a>Avantages du magasin d'objets blob distants  
 Le magasin d'objets blob distants possède les avantages suivants :  
  
### <a name="optimized-database-storage-and-performance"></a>Performances et stockage de base de données optimisés  
 Le stockage d'objets blob dans la base de données peut consommer une grande quantité d'espace de fichiers et se révéler coûteuse du point de vue des ressources de serveur. Le magasin d'objets blob distants transmet de manière efficace les objets blob à la solution de stockage de votre choix, et en stocke les références dans la base de données. Cela permet de libérer de l'espace de stockage serveur pour les données structurées, ainsi que des ressources serveur pour les opérations de base de données.  
  
### <a name="efficient-management-of-blobs"></a>Gestion efficace des objets blob  
 La gestion des objets blob stockés est prise en charge par plusieurs fonctionnalités du magasin d'objets blob distants :  
  
-   Les objets blob sont gérés à l'aide des transactions ACID (Atomicité, Cohérence, Isolation et Durabilité).  
  
-   Les objets blob sont organisés en collections.  
  
-   Le nettoyage de la mémoire, la vérification de la cohérence et les autres fonctions de maintenance y sont inclus.  
  
### <a name="standardized-api"></a>API standardisée  
 RBS définit un ensemble d'API qui fournit un modèle de programmation standardisé permettant aux applications d'accéder à tous les magasins d'objets blob et de les modifier. Chaque magasin d'objets blob peut spécifier sa propre bibliothèque de fournisseur, connectée à la bibliothèque cliente RBS et spécifiant la manière dont les objets blob sont stockés et accessibles.  
  
 Certains fournisseurs de solutions de stockage tiers ont développé des fournisseurs RBS qui sont conformes à ces API standard et qui prennent en charge le stockage d'objets blob sur différentes plateformes de stockage.  
  
## <a name="rbs-requirements"></a>Conditions requises du magasin d'objets blob distants (RBS)  
 Le magasin d'objets blob distants nécessite [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise pour le serveur de base de données principal sur lequel les métadonnées d'objets blob sont stockées. Cependant, si vous utilisez le fournisseur FILESTREAM fourni, vous pouvez stocker les objets blob sur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard.  
  
 Le magasin d'objets blob distants comprend un fournisseur FILESTREAM qui vous permet de stocker les objets blob sur une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous souhaitez utiliser le magasin d'objets blob distants pour stocker des objets blob dans une solution de stockage différente, vous devez utiliser un fournisseur RBS tiers, qui aura été développé pour cette solution de stockage particulière, ou bien développer un fournisseur RBS personnalisé à l'aide de l'API RBS. Un exemple de fournisseur stockant des objets blob sur un système de fichiers NTFS est disponible parmi les ressources pédagogiques du site [CodePlex](https://go.microsoft.com/fwlink/?LinkId=210190).  
  
## <a name="rbs-security"></a>Sécurité relative au magasin d'objets blob distants (RBS)  
 Lorsque vous utilisez un fournisseur personnalisé pour stocker des objets blob en dehors de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les objets blob peuvent être disponibles pour d'autres processus contournant le système de sécurité de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Assurez-vous de protéger les objets blob stockés à l'aide d'autorisations et d'options de chiffrement convenant au support de stockage utilisé par le fournisseur personnalisé.  
  
##  <a name="rbs-resources"></a><a name="rbsresources"></a>Ressources RBS  
 **Documentation relative au magasin d'objets blob distants (RBS)**  
 La documentation relative au magasin d'objets blob distants (RBS) est comprise dans le package Windows Installer. Si vous souhaitez consulter la documentation relative au magasin d'objets blob distants sans installer ce dernier, vous pouvez consulter la version [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] de la documentation [en ligne sur le site MSDN Library](https://go.microsoft.com/fwlink/?LinkId=210192).  
  
 **Livre blanc du magasin d'objets blob distants (RBS)**  
 Le livre blanc «[Stockage étendu des objets blob](https://go.microsoft.com/fwlink/?LinkId=210422)», disponible au téléchargement sous la forme d'un document Microsoft Word, fournit des informations détaillées à propos de l'installation et de la configuration du magasin d'objets blob distants.  
  
 **Exemples de magasins d'objets blob distants (RBS)**  
 Les exemples de magasins d'objets blob distants (RBS) disponibles sur le site [CodePlex](https://go.microsoft.com/fwlink/?LinkId=210190) montrent comment développer une application RBS et comment développer et installer un fournisseur RBS personnalisé.  
  
 **Blog du magasin d'objets blob distants (RBS)**  
 Le [blog du magasin d'objets blob distants (RBS)](https://go.microsoft.com/fwlink/?LinkId=210315) fournit des informations supplémentaires qui vous aideront à mieux comprendre, déployer et gérer les magasins d'objets blob distants.  
  
  
