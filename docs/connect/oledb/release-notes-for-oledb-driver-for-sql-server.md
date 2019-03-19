---
title: Notes de publication (OLE DB Driver pour SQL Server) | Microsoft Docs
ms.date: 02/13/2019
ms.prod: sql
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: genemi
author: mateusz-kmiecik
ms.author: v-makmie
ms.openlocfilehash: 2a1d6d216f4f7ec7fee0f5f9aa5810c78f1936e6
ms.sourcegitcommit: 03870f0577abde3113e0e9916cd82590f78a377c
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2019
ms.locfileid: "58161766"
---
# <a name="release-notes-for-the-microsoft-ole-db-driver-for-sql-server"></a>Notes de publication de Microsoft OLE DB Driver, pour SQL Server

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

Cette page explique ce qui a été ajouté dans chaque version du pilote Microsoft OLE DB pour SQL Server.

<!--
USE THE TABLE FORMAT!
Hello, from now on, please use the table-based format standard for all new Release Notes content.
See section "## 18.2.1" for a live example in this article.
Thank you. For questions, contact GeneMi. (2019/03/16)
-->

## <a name="1821"></a>18.2.1

<!--
USE THE TABLE FORMAT!
Hello, from now on, please use the table-based format standard for all new Release Notes content.
See section "## 18.2.1" for a live example in this article.
Thank you. For questions, contact GeneMi. (2019/03/16)
-->

Février 2019

### <a name="features-added"></a>Fonctionnalités ajoutées

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| Prise en charge l’encodage UTF-8 du serveur. | &bull; &nbsp; [Prise en charge d’UTF-8 dans OLE DB Driver pour SQL Server](features/utf-8-support-in-oledb-driver-for-sql-server.md). |
| Prise en charge de l’authentification Azure Active Directory. | &bull; &nbsp; [Utilisation d’Azure Active Directory](features/using-azure-active-directory.md). |
| &nbsp; | &nbsp; |

## <a name="1810"></a>18.1.0

Juillet 2018

### <a name="features-added"></a>Fonctionnalités ajoutées

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| Prise en charge pour le `UseFMTONLY` mot clé de chaîne de connexion et pour le `SSPROP_INIT_USEFMTONLY` propriété d’initialisation. | `UseFMTONLY` contrôle la façon dont les métadonnées sont récupérées lors de la connexion à [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] et les versions ultérieures.<br/><br/>&bull; &nbsp; [Utilisation de mots clés de chaîne de connexion avec OLE DB Driver pour SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

### <a name="bugs-fixed"></a>Bogues corrigés

| Bogue corrigé | Détails |
| :-------- | :------ |
| Fixe de version incorrecte du fichier de format BCP. | 18.0 le pilote OLE DB définit incorrectement la version du fichier de format BCP à 18.0, au lieu de vers 11.0.<br/><br/>Impossible de lire les fichiers de format générés par le 18.0 du pilote OLE DB par 18.1 le pilote OLE DB.<br/><br/>Si vous avez besoin d’utiliser des fichiers de format générés par la version précédente du pilote avec le nouveau pilote, vous pouvez modifier manuellement les fichiers pour remplacer la version 11.0. |
| &nbsp; | &nbsp; |

## <a name="1802"></a>18.0.2

### <a name="features-added"></a>Fonctionnalités ajoutées

| Fonctionnalité ajoutée | Détails |
| :------------ | :------ |
| Prise en charge pour le `MultiSubnetFailover` mot clé de chaîne de connexion et le `SSPROP_INIT_MULTISUBNETFAILOVER` propriété d’initialisation. | &bull; &nbsp; [Prise en charge de la reprise d’activité et de la haute disponibilité par OLE DB Driver pour SQL Server](features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md).<br/><br/>&bull; &nbsp; [Utilisation de mots clés de chaîne de connexion avec OLE DB Driver pour SQL Server](applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md). |
| &nbsp; | &nbsp; |

## <a name="see-also"></a>Voir aussi

[Microsoft OLE DB Driver pour SQL Server](oledb-driver-for-sql-server.md)
