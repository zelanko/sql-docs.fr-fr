---
title: Composants de SQL Server Native Client (fr) Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], components
- components [SQL Server Native Client]
- SQLNCLI, about SQL Server Native Client
ms.assetid: 65f932d5-daa1-4eff-b6df-ee633fcf2a7c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bae5a3871750791d3339e2b98b715ec3779d105d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302506"
---
# <a name="components-of-sql-server-native-client"></a>Composants de SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client contient les composants suivants :  
  
|Composant|Description|  
|---------------|-----------------|  
|sqlncli11.dll|Fichier DDL (Dynamic-Link Library) contenant l'ensemble des fonctionnalités [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Sont inclus le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client et le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|sqlnclir11.rll|Fichier de ressources d'accompagnement pour la bibliothèque [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|   
|sqlncli.h|En-tête de fichier [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client contenant toutes les nouvelles définitions nécessaires pour pouvoir utiliser [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Ce fichier d'en-tête remplace les fichiers odbcss.h et sqloledb.h.<br /><br /> Note: Vous ne pouvez pas référence sqlncli.h et odbcss.h dans le même programme, mais vous pouvez référence sqlncli.h et sqloledb.h dans le même programme aussi longtemps que sqloledb.h est défini en premier.|  
|sqlncli11.lib|Le dossier de la bibliothèque devait appeler directement les [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fonctions **d’utilité bcp** qui font partie du conducteur de l’ODBC du client autochtone.<br /><br /> Remarque : Si vous faites référence au fichier sqlncli11.lib dans votre code de programmation, vous devez vous assurer que le fichier sqlncli11.dll est dans votre trajectoire de système, et dans la trajectoire du système des utilisateurs qui font usage de votre application.|  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d'applications avec SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
