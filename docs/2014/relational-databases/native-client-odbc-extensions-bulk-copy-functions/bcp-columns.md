---
title: bcp_columns | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- bcp_columns
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_columns function
ms.assetid: 5376f6fe-9508-439a-8c66-778d77f19ac3
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f2f7cb508f9b7715abbc2505f38b30795df2d142
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36040627"
---
# <a name="bcpcolumns"></a>bcp_columns
  Définit le nombre total de colonnes trouvées dans le fichier utilisateur pour une utilisation avec une copie en bloc vers ou depuis [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [bcp_setbulkmode](bcp-setbulkmode.md) peut être utilisé au lieu de bcp_columns et [bcp_colfmt](bcp-colfmt.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RETCODE bcp_columns (  
HDBC   
hdbc  
,  
INT   
nColumns  
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *pas*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
 *nColumns*  
 Nombre total de colonnes dans le fichier utilisateur. Même si vous vous apprêtez à la copie de données à partir du fichier utilisateur à un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table et n’envisagez pas de copier toutes les colonnes dans le fichier utilisateur, vous devez toujours définir *nColumns* au nombre total de colonnes du fichier utilisateur.  
  
## <a name="returns"></a>Valeur renvoyée  
 SUCCEED ou FAIL.  
  
## <a name="remarks"></a>Notes  
 Cette fonction peut être appelée uniquement après [bcp_init](bcp-init.md) a été appelé avec un nom de fichier valide.  
  
 Vous devez appeler cette fonction uniquement si vous envisagez d'utiliser un format de fichier utilisateur qui diffère du format par défaut. Pour plus d’informations sur une description du format de fichier utilisateur par défaut, consultez **bcp_init**.  
  
 Après avoir appelé `bcp_columns`, vous devez appeler [bcp_colfmt](bcp-colfmt.md)pour chaque colonne dans le fichier utilisateur afin de définir complètement un format de fichier personnalisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de copie en bloc](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  