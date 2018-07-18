---
title: Notes de publication (OLE DB Driver pour SQL Server) | Microsoft Docs
ms.date: 07/03/2018
ms.prod: sql
ms.suite: sql
ms.technology: connectivity
ms.topic: conceptual
author: David-Engel
ms.author: v-daveng
ms.openlocfilehash: 698ac0a38edb55bca36c2d7dc15c9c7c2faf3efe
ms.sourcegitcommit: 368a7f7e9d860f9407a5a013e135f29f27efcd02
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37872889"
---
# <a name="release-notes-for-the-microsoft-ole-db-driver-for-sql-server"></a>Notes de publication de Microsoft OLE DB Driver pour SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

Cette page explique ce qui a été ajouté dans chaque version du pilote Microsoft OLE DB pour SQL Server.

## <a name="whats-new-in-version-1810"></a>Nouveautés de la version 18.1.0

**Fonctionnalités ajoutées :**

* Prise en charge de `UseFMTONLY` mot clé de chaîne de connexion et `SSPROP_INIT_USEFMTONLY` propriété d’initialisation.
`UseFMTONLY` contrôle la façon dont les métadonnées sont récupérées lors de la connexion à [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et les versions ultérieures.  
Pour plus d'informations, consultez :
  * [Utilisation de mots clés de chaîne de connexion avec OLE DB Driver pour SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)

**Bogues corrigés :**

* Fixe de version incorrecte du fichier de format BCP. 18.0 le pilote OLE DB définit incorrectement la version du fichier de format BCP sur 18.0 au lieu de 11.0. Impossible de lire les fichiers de format générés par le 18.0 du pilote OLE DB par 18.1 le pilote OLE DB. Si vous avez besoin d’utiliser des fichiers de format générés par la version précédente du pilote avec le nouveau pilote, vous pouvez modifier manuellement les fichiers pour remplacer la version 11.0.

## <a name="whats-new-in-version-1802"></a>Nouveautés de la version 18.0.2

**Fonctionnalités ajoutées**:

* Prise en charge de `MultiSubnetFailover` mot clé de chaîne de connexion et `SSPROP_INIT_MULTISUBNETFAILOVER` propriété d’initialisation.  
Pour plus d'informations, consultez :  
  * [Prise en charge de la récupération d’urgence et de la haute disponibilité par OLE DB Driver pour SQL Server](features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)  
  * [Utilisation de mots clés de chaîne de connexion avec OLE DB Driver pour SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)

## <a name="see-also"></a>Voir aussi
[Microsoft OLE DB Driver pour SQL Server](oledb-driver-for-sql-server.md)
