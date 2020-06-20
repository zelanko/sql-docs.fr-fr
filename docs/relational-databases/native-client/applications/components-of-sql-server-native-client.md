---
title: Components
description: En savoir plus sur les composants de la SQL Server Native Client tels que sqlncli11.dll, sqlnclir11. rll, sqlncli. h et SQLNCLI11. lib.
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
ms.openlocfilehash: f298c7e3c453da1a20826d91509ca61778ad65b0
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84965185"
---
# <a name="components-of-sql-server-native-client"></a>Composants de SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client contient les composants suivants :  
  
|Composant|Description|  
|---------------|-----------------|  
|sqlncli11.dll|Fichier DDL (Dynamic-Link Library) contenant l'ensemble des fonctionnalités [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Sont inclus le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client et le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|sqlnclir11.rll|Fichier de ressources d'accompagnement pour la bibliothèque [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|   
|sqlncli.h|En-tête de fichier [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client contenant toutes les nouvelles définitions nécessaires pour pouvoir utiliser [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Ce fichier d'en-tête remplace les fichiers odbcss.h et sqloledb.h.<br /><br /> Remarque : vous ne pouvez pas référencer sqlncli. h et odbcss. h dans le même programme, mais vous pouvez faire référence à sqlncli. h et SQLOLEDB. h dans le même programme tant que sqloledb. h est défini en premier.|  
|sqlncli11.lib|Fichier de bibliothèque nécessaire pour appeler directement les fonctions de l’utilitaire **BCP** qui font partie du [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client.<br /><br /> Remarque : Si vous référencez le fichier SQLNCLI11. lib dans votre code de programmation, vous devez vous assurer que le fichier sqlncli11.dll se trouve dans votre chemin d’accès système et dans le chemin d’accès système des utilisateurs qui utilisent votre application.|  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’applications avec SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
