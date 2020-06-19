---
title: Stratégies de prise en charge
description: En savoir plus sur SQL Server Native Client versions de SQL Server, les systèmes d’exploitation et les stratégies de prise en charge pour ADO, BCP, ODBC et OLE DB.
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.custom: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 09c80cf4-23e6-4027-a24f-cdb9c87af811
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 621cd2345f578b4f1a6091450d3e4a1c5697682b
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965196"
---
# <a name="support-policies-for-sql-server-native-client"></a>Stratégies de prise en charge pour SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Cette rubrique décrit les façons dont différents composants d'accès aux données peuvent être utilisés avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="server-support"></a>Prise en charge de serveur  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client 11,0 prend en charge les connexions à,,,, [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] et [!INCLUDE[ssSDSfull](../../../includes/sssdsfull-md.md)] .  
  
## <a name="supported-operating-system-versions"></a>Versions de système d’exploitation prises en charge  
 Le tableau suivant répertorie les systèmes d'exploitation qui prennent en charge [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
|Version de SQL Server Native Client|Systèmes d’exploitation pris en charge|  
|--------------------------------------|---------------------------------|  
|SQL Server Native Client (SQL Server 2005)|Microsoft Windows 2000 Service Pack 4 ou version ultérieure<br /><br /> Microsoft Windows Server 2003 ou version ultérieure<br /><br /> Microsoft Windows XP Service Pack 1 ou version ultérieure<br /><br /> Microsoft Windows Vista (requiert [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Service Pack 2, ou version ultérieure)<br /><br /> Microsoft Windows Server 2008 R2 (nécessite le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Service Pack 2 ou version ultérieure)|  
|SQL Server Native Client 10,0 ( [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] )|Microsoft Windows Server 2003 Service Pack 2, ou version ultérieure<br /><br /> Microsoft Windows XP Service Pack 2 ou version ultérieure<br /><br /> Microsoft Windows Vista<br /><br /> Microsoft Windows Server 2008 R2|  
|SQL Server Native Client 10,5 ( [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] )|Microsoft Windows Server 2003 Service Pack 2, ou version ultérieure<br /><br /> Microsoft Windows XP Service Pack 2 ou version ultérieure<br /><br /> Microsoft Windows Vista<br /><br /> Microsoft Windows Server 2008 R2<br /><br /> Microsoft Windows 7|  
|SQL Server Native Client 11.0 ([!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] et [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)])|Microsoft Windows Vista<br /><br /> Microsoft Windows Server 2008 R2<br /><br /> Microsoft Windows 7<br /><br /> Microsoft Windows 8<br /><br /> Microsoft Windows Server 2012|  
  
## <a name="ado-support-policies"></a>Stratégies de prise en charge ADO  
 Les applications ADO peuvent utiliser le fournisseur OLE DB SQLOLEDB fourni avec Windows si elles n'ont pas besoin des fonctionnalités de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou version ultérieure.  
  
 Les applications ADO peuvent utiliser la version de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] native client incluse dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] . Les applications ADO peuvent également utiliser [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 (fourni avec [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)]), mais dans ce cas elles doivent spécifier `DataTypeCompatibility=80` dans les chaînes de connexion. Seules les fonctionnalités de [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] sont disponibles lorsque `DataTypeCompatibility=80` est présent dans les chaînes de connexion.  
  
## <a name="bcp-support-policies"></a>Stratégies de prise en charge BCP  
 À compter de [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], bcp.exe prend en charge les fichiers de données qui ne sont pas plus de trois versions de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] de moins que la version de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avec laquelle bcp.exe a été fourni.  
  
## <a name="odbc-support-policies"></a>Stratégies de prise en charge ODBC  
 Les applications doivent utiliser le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fourni avec le système d'exploitation Windows. Vous pouvez utiliser le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client si l'application est certifiée pour une utilisation avec une version spécifique de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="ole-db-support-policies"></a>Stratégies de prise en charge OLE DB  
 Les applications doivent utiliser le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fourni avec le système d'exploitation Windows. Vous pouvez utiliser le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client si l'application est certifiée pour une utilisation avec une version spécifique de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
 Les applications OLE DB qui n'ont pas été certifiées pour une utilisation avec [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client peuvent utiliser [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native client si elles spécifient `DataTypeCompatibility=80` dans leurs chaînes de connexion.  
  
 Les applications OLE DB qui utilisent OLE DB Service Components peuvent utiliser [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native client uniquement si elles spécifient `DataTypeCompatibility=80` dans leurs chaînes de connexion. Toutefois, aucune fonctionnalité ajoutée après [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ne sera disponible dans ce cas.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’applications avec SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
