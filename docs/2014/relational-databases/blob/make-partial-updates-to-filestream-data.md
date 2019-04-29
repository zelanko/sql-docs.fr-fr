---
title: Effectuer des mises à jour partielles de données FILESTREAM | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
- FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
ms.assetid: d6f7661e-6c14-4d31-9541-4520ca0f82b2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: cce625b931fda4e70ad67c6e5940c93604c81776
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920099"
---
# <a name="make-partial-updates-to-filestream-data"></a>Effectuer des mises à jour partielles de données FILESTREAM
  Une application utilise FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT pour appliquer des mises à jour partielles aux données BLOB FILESTREAM. La fonction [DeviceIoControl](https://go.microsoft.com/fwlink/?LinkId=105527) passe cette valeur et le descripteur qui est retourné d’ [OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md) au pilote FILESTREAM. Le pilote force ensuite une copie côté serveur des données FILESTREAM actuelles dans le fichier référencé par le descripteur. Si l'application publie la valeur FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT après l'écriture dans le descripteur, la dernière opération d'écriture persistera et les opérations d'écriture antérieures effectuées dans le descripteur seront perdues.  
  
> [!NOTE]  
>  FILESTREAM compte sur le [protocole SMB](https://go.microsoft.com/fwlink/?LinkId=112454) pour l’accès à distance.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant vous indique comment utiliser la valeur `FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT` pour effectuer une mise à jour partielle d'un BLOB FILESTREAM inséré.  
  
> [!NOTE]  
>  Cet exemple nécessite la base de données compatible FILESTREAM et la table qui sont créées dans [Créer une base de données compatible FILESTREAM](create-a-filestream-enabled-database.md) et [Créer une table pour le stockage de données FILESTREAM](create-a-table-for-storing-filestream-data.md).  
  
 [!code-cpp[FILESTREAM#FS_CPP_FSCTL](../../snippets/tsql/SQL15/tsql/filestream/cpp/filestream.cpp#fs_cpp_fsctl)]  
  
## <a name="see-also"></a>Voir aussi  
 [Accéder à des données FILESTREAM avec OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md)   
 [Créer des applications clientes pour les données FILESTREAM](create-client-applications-for-filestream-data.md)  
  
  
