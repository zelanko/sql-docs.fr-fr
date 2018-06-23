---
title: Effectuer des mises à jour partielles de données FILESTREAM | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-blob
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FILESTREAM [SQL Server], FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
- FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
ms.assetid: d6f7661e-6c14-4d31-9541-4520ca0f82b2
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c59d3e7823efe62ecb7227eab605af23a6ea3112
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36038593"
---
# <a name="make-partial-updates-to-filestream-data"></a>Effectuer des mises à jour partielles de données FILESTREAM
  Une application utilise FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT pour appliquer des mises à jour partielles aux données BLOB FILESTREAM. La fonction [DeviceIoControl](http://go.microsoft.com/fwlink/?LinkId=105527) passe cette valeur et le descripteur qui est retourné d’ [OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md) au pilote FILESTREAM. Le pilote force ensuite une copie côté serveur des données FILESTREAM actuelles dans le fichier référencé par le descripteur. Si l'application publie la valeur FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT après l'écriture dans le descripteur, la dernière opération d'écriture persistera et les opérations d'écriture antérieures effectuées dans le descripteur seront perdues.  
  
> [!NOTE]  
>  FILESTREAM compte sur le [protocole SMB](http://go.microsoft.com/fwlink/?LinkId=112454) pour l’accès à distance.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant vous indique comment utiliser la valeur `FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT` pour effectuer une mise à jour partielle d'un BLOB FILESTREAM inséré.  
  
> [!NOTE]  
>  Cet exemple nécessite la base de données compatible FILESTREAM et la table qui sont créées dans [Créer une base de données compatible FILESTREAM](create-a-filestream-enabled-database.md) et [Créer une table pour le stockage de données FILESTREAM](create-a-table-for-storing-filestream-data.md).  
  
 [!code-cpp[FILESTREAM#FS_CPP_FSCTL](../../snippets/tsql/SQL15/tsql/filestream/cpp/filestream.cpp#fs_cpp_fsctl)]  
  
## <a name="see-also"></a>Voir aussi  
 [Accéder à des données FILESTREAM avec OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md)   
 [Créer des applications clientes pour les données FILESTREAM](create-client-applications-for-filestream-data.md)  
  
  