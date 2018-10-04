---
title: bcp_getcolfmt | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_getcolfmt
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_getcolfmt function
ms.assetid: f8bdada5-7b2d-4475-8c98-f93e9d77b130
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: db8b433652829b16890552a70bd1e0d08d1c1bc4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48137904"
---
# <a name="bcpgetcolfmt"></a>bcp_getcolfmt
  Utilisé pour rechercher la valeur de la propriété de format de colonne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RETCODE bcp_getcolfmt (  
HDBC   
hdbc  
,  
INT   
field  
,  
INT   
property  
,  
void*   
pValue  
,  
INT   
cbvalue,  
INT*   
pcbLen  
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *pas*  
 Handle de connexion ODBC compatible avec la copie en bloc.  
  
 *field*  
 Numéro de colonne pour lequel la propriété est extraite.  
  
 *property*  
 L'une des constantes de propriété.  
  
 *pValue*  
 Pointeur vers la mémoire tampon de laquelle la valeur de la propriété doit être extraite.  
  
 *cbValue*  
 Taille de la mémoire tampon de propriété, en octets.  
  
 *pcbLen*  
 Pointeur vers la longueur des données retournées dans la mémoire tampon de propriété.  
  
## <a name="returns"></a>Valeur renvoyée  
 SUCCEED ou FAIL.  
  
## <a name="remarks"></a>Notes  
 Les valeurs de propriété de format de colonne sont répertoriées dans le [bcp_setcolfmt](bcp-setcolfmt.md) rubrique. Ces valeurs sont définies en appelant la fonction **bcp_setcolfmt** . La fonction **bcp_getcolfmt** est utilisée pour rechercher la valeur de la propriété de format de colonne.  
  
 Changements de comportement peuvent être observés lors de la connexion à un [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] (ou version ultérieure) ordinateur du serveur, par rapport aux versions [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions. Pour plus d’informations, consultez [Découverte des métadonnées](../native-client/features/metadata-discovery.md).  
  
## <a name="bcpgetcolfmt-support-for-enhanced-date-and-time-features"></a>Prise en charge  par bcp_getcolfmt des fonctionnalités de date et heure améliorées  
 Les types utilisés avec la `BCP_FMT_TYPE` sont de propriété pour les types date/heure comme spécifié dans [modifications de copie en bloc pour les Types améliorées de Date / heure &#40;OLE DB et ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).  
  
 Pour plus d’informations, consultez [améliorations Date / heure &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de copie en bloc](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
