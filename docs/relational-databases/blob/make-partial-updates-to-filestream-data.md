---
title: Effectuer des mises à jour partielles de données FILESTREAM | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
- FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
ms.assetid: d6f7661e-6c14-4d31-9541-4520ca0f82b2
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: fbc9f9d7cba88021c2a3d4939ea21ae91b69ee97
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68125159"
---
# <a name="make-partial-updates-to-filestream-data"></a>Effectuer des mises à jour partielles de données FILESTREAM
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Une application utilise FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT pour appliquer des mises à jour partielles aux données BLOB FILESTREAM. La fonction [DeviceIoControl](https://go.microsoft.com/fwlink/?LinkId=105527) passe cette valeur et le descripteur qui est retourné d’ [OpenSqlFilestream](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md) au pilote FILESTREAM. Le pilote force ensuite une copie côté serveur des données FILESTREAM actuelles dans le fichier référencé par le descripteur. Si l'application publie la valeur FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT après l'écriture dans le descripteur, la dernière opération d'écriture persistera et les opérations d'écriture antérieures effectuées dans le descripteur seront perdues.  
  
> [!NOTE]  
>  FILESTREAM compte sur le [protocole SMB](https://go.microsoft.com/fwlink/?LinkId=112454) pour l’accès à distance.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant vous indique comment utiliser la valeur `FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT` pour effectuer une mise à jour partielle d'un BLOB FILESTREAM inséré.  
  
> [!NOTE]  
>  Cet exemple nécessite la base de données compatible FILESTREAM et la table qui sont créées dans [Créer une base de données compatible FILESTREAM](../../relational-databases/blob/create-a-filestream-enabled-database.md) et [Créer une table pour le stockage de données FILESTREAM](../../relational-databases/blob/create-a-table-for-storing-filestream-data.md).  
  
 [!code-cpp[FILESTREAM#FS_CPP_FSCTL](../../relational-databases/blob/codesnippet/cpp/make-partial-updates-to-_1.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Accéder à des données FILESTREAM avec OpenSqlFilestream](../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)   
 [Créer des applications clientes pour les données FILESTREAM](../../relational-databases/blob/create-client-applications-for-filestream-data.md)  
  
  
