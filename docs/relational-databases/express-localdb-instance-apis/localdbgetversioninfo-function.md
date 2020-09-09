---
description: Fonction LocalDBGetVersionInfo
title: LocalDBGetVersionInfo fonction) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
apiname:
- LocalDBGetVersionInfo
apilocation:
- sqluserinstance.dll
apitype: DLLExport
ms.assetid: d4aaea30-1d0d-4436-bcdc-5c101d27b1c1
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 6776f1ce1d5cb92bba4d570a53c95f351b501960
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89542929"
---
# <a name="localdbgetversioninfo-function"></a>Fonction LocalDBGetVersionInfo
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Retourne des informations pour la version spécifiée de SQL Server Express LocalDB, notamment si elle existe, ainsi que le numéro de version complet de LocalDB (avec les numéros de build et de version).  
  
 Les informations sont retournées sous la forme d’un **struct** nommé **LocalDBVersionInfo**, qui a la définition suivante.  
  
```  
typedef struct _LocalDBVersionInfo  
{  
      // Contains the size of the LocalDBVersionInfo struct  
      DWORD  cbLocalDBVersionInfoSize;  
  
      // Holds the version name  
      TLocalDBVersionwszVersion;  
  
      // TRUE if the instance files exist on disk, FALSE otherwise  
      BOOL   bExists;  
  
      // Holds the LocalDB version for the instance in the format: major.minor.build.revision  
      DWORD  dwMajor;  
      DWORD  dwMinor;  
      DWORD  dwBuild;  
      DWORD  dwRevision;  
} LocalDBVersionInfo;  
  
```  
  
 **Fichier d'en-tête :** sqlncli.h  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LocalDBGetVersionInfo(  
           PCWSTR wszVersionName,           PLocalDBVersionInfo pVersionInfo,           DWORD dwVersionInfoSize);  
```  
  
## <a name="parameters"></a>Paramètres  
 *wszVersionName*  
 [Entrée] Le nom de version de LocalDB.  
  
 *pVersionInfo*  
 [Sortie] La mémoire tampon pour stocker des informations sur la version de LocalDB.  
  
 *dwVersionInfoSize*  
 Entrée Contient la taille de la mémoire tampon *VERSIONINFO* .  
  
## <a name="returns"></a>Retours  
 S_OK  
 La fonction a réussi.  
  
 [LOCALDB_ERROR_NOT_INSTALLED](../../relational-databases/express-localdb-error-messages/localdb-error-not-installed.md)  
 SQL Server Express LocalDB n'est pas installé sur l'ordinateur.  
  
 [LOCALDB_ERROR_INVALID_PARAMETER](../../relational-databases/express-localdb-error-messages/localdb-error-invalid-parameter.md)  
 Un ou plusieurs paramètres d'entrée spécifiés ne sont pas valides.  
  
 [LOCALDB_ERROR_UNKNOWN_VERSION](../../relational-databases/express-localdb-error-messages/localdb-error-unknown-version.md)  
 La version spécifiée de LocalDB n'existe pas.  
  
 [LOCALDB_ERROR_INTERNAL_ERROR](../../relational-databases/express-localdb-error-messages/localdb-error-internal-error.md)  
 Une erreur inattendue s’est produite. Pour plus d'informations, consultez le journal des événements.  
  
## <a name="details"></a>Détails  
 Le raisonnement derrière l’introduction de l’argument de taille de **struct** (*lpVersionInfoSize*) consiste à permettre à l’API de retourner différentes versions du **LocalDBVersionInfostruct**, ce qui permet de garantir une compatibilité ascendante et descendante.  
  
 Si l’argument de taille de **struct** (*lpVersionInfoSize*) correspond à la taille d’une version connue du **LocalDBVersionInfostruct**, cette version du **struct** est retournée. Sinon, LOCALDB_ERROR_INVALID_PARAMETER est retourné.  
  
 Voici un exemple typique d’utilisation de l’API **LocalDBGetVersionInfo** :  
  
```  
LocalDBVersionInfo vi;  
LocalDBVersionInfo(L"11.0", &vi, sizeof(LocalDBVersionInfo));  
  
```  
  
## <a name="remarks"></a>Notes  
 Pour un exemple de code qui utilise l'API LocalDB, consultez [SQL Server Express LocalDB Reference](../../relational-databases/sql-server-express-localdb-reference.md).  
  
## <a name="see-also"></a>Voir aussi  
 [En-tête et informations de version SQL Server Express LocalDB](../../relational-databases/express-localdb-instance-apis/sql-server-express-localdb-header-and-version-information.md)  
  
  
