---
description: setBytes, méthode (long, byte)
title: Méthode setBytes (long, octet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerBlob.setBytes (long.byte[])
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ffb8f107-0f9d-4410-957f-62b718e1e872
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d7c81dc36f8dbb917634404ddeceb35db16f36ae
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88432341"
---
# <a name="setbytes-method-long-byte"></a>setBytes, méthode (long, byte)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Enregistre le tableau d'octets spécifié dans le BLOB, en démarrant à la position spécifiée, puis retourne le nombre d'octets écrits.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int setBytes(long pos,  
                    byte[] bytes)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *pos*  
  
 Position (base 1) dans le BLOB à laquelle démarrer l'écriture des données.  
  
 *bytes*  
  
 Tableau d'octets à écrire dans le BLOB.  
  
## <a name="return-value"></a>Valeur de retour  
 Valeur **long** spécifiant le nombre d’octets écrits.  
  
## <a name="exceptions"></a>Exceptions  
 java.sql.SQLException  
  
## <a name="remarks"></a>Notes  
 Cette méthode setBytes est spécifiée par la méthode setBytes de l’interface java.sql.Blob.  
  
 Les données sont remplacées à partir de la position spécifiée et peuvent dépasser la longueur initiale du BLOB. La spécification d'une valeur position+1 permet d'ajouter des octets. Le passage d'une valeur position+2 ou supérieure (ou inférieure ou égale à zéro) génère une erreur de position. Si un tableau **d’octets** de longueur zéro est transmis, la méthode retourne zéro, car aucun octet n’a été écrit.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode setBytes &#40;SQLServerBlob&#41;](../../../connect/jdbc/reference/setbytes-method-sqlserverblob.md)   
 [SQLServerBlob, méthodes](../../../connect/jdbc/reference/sqlserverblob-methods.md)   
 [SQLServerBlob, membres](../../../connect/jdbc/reference/sqlserverblob-members.md)   
 [SQLServerBlob, classe](../../../connect/jdbc/reference/sqlserverblob-class.md)  
  
  
