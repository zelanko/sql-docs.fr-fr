---
title: Composants de SQL Server Native Client | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 60dc57c4078e580cfae3918c42721ddc49089af2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47633337"
---
# <a name="components-of-sql-server-native-client"></a>Composants de SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client contient les composants suivants :  
  
|Composant|Description|  
|---------------|-----------------|  
|sqlncli11.dll|Fichier DDL (Dynamic-Link Library) contenant l'ensemble des fonctionnalités [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Sont inclus le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client et le pilote ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|  
|sqlnclir11.rll|Fichier de ressources d'accompagnement pour la bibliothèque [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.|   
|sqlncli.h|En-tête de fichier [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client contenant toutes les nouvelles définitions nécessaires pour pouvoir utiliser [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. Ce fichier d'en-tête remplace les fichiers odbcss.h et sqloledb.h.<br /><br /> Remarque : Vous ne pouvez pas référencer sqlncli.h et odbcss.h dans le même programme, mais vous pouvez référencer sqlncli.h et sqloledb.h dans même programme tant que sqloledb.h soit défini en premier.|  
|sqlncli11.lib|Le fichier bibliothèque nécessaire pour appeler directement la **bcp** fonctions utilitaires qui font partie de la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client.<br /><br /> Remarque : Si vous référencez le fichier sqlncli11.lib dans votre code de programmation, vous devez vous assurer que le fichier sqlncli11.dll est dans votre chemin système et dans le chemin d’accès système des utilisateurs qui emploient votre application.|  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’applications avec SQL Server Native Client](../../../relational-databases/native-client/applications/building-applications-with-sql-server-native-client.md)  
  
  
