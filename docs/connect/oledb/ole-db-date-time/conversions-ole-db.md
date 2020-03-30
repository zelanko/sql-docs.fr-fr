---
title: Liaisons et conversions (OLE DB) | Microsoft Docs
description: Liaisons et conversions (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB]
- bindings [OLE DB]
- OLE DB, bindings and conversions
author: pmasl
ms.author: pelopes
ms.openlocfilehash: dc86193f40474fc373c1b0e7dd48e579e8548821
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "68015839"
---
# <a name="conversions-ole-db"></a>Conversions (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Cette section explique comment effectuer une conversion entre les valeurs **datetime** et **datetimeoffset**. Les conversions décrites dans cette section sont soit déjà fournies par OLE DB, soit une extension cohérente de ce dernier.  
  
 Le format des littéraux et des chaînes pour les dates et les heures dans OLE DB suit généralement la norme ISO et ne dépend pas des paramètres régionaux du client. Une exception est DBTYPE_DATE où la norme est OLE Automation. Toutefois, du fait qu’OLE DB Driver pour SQL Server effectue uniquement des conversions entre des types lorsque des données sont transmises vers ou depuis le client, il n'existe aucun moyen de contraindre OLE DB Driver pour SQL Server à effectuer des conversions entre DBTYPE_DATE et un format de chaîne. Sinon, les chaînes utilisent les formats suivants (le texte entre crochets indique un élément facultatif) :  
  
-   Le format des chaînes **datetime** et **datetimeoffset** est le suivant :  
  
     *yyyy*-*mm*-*dd*[ *hh*:*mm*:*ss*[.*9999999*][ ± *hh*:*mm*]]  
  
-   Le format des chaînes **time** est :  
  
     *hh*:*mm*:*ss*[.*9999999*]  
  
-   Le format des chaînes **date** est :  
  
     *aaaa*-*mm*-*jj*  
  
> [!NOTE]  
>  Les versions antérieures de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client et SQLOLEDB autorisaient l'implémentation de conversions OLE en cas d'échec des processus de conversion standard. OLE DB Driver pour SQL Server suit le même comportement que [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client. C'est pourquoi certaines conversions réalisées par OLE DB Driver pour SQL Server et versions ultérieures diffèrent de la spécification OLE DB.  
  
 Les conversions de chaînes autorisent une souplesse en matière d'espace et de largeur de champ. Pour plus d'informations, consultez la section « Formats de données : chaînes et littéraux » dans [Prise en charge des types de données pour les améliorations de date et d’heure OLE DB](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md).  
  
 Les règles suivantes sont les règles générales de conversion :  
  
-   Lorsqu'une chaîne est convertie en type date/heure, la chaîne est d'abord analysée en tant que littéral ISO. En cas d'échec, la chaîne est analysée comme un littéral de date OLE doté de composants heure.  
  
-   Si aucune heure n'est fournie mais le récepteur peut stocker l'heure, l'heure est définie avec la valeur zéro. Si aucune date n'est fournie mais le récepteur peut stocker une date, la date définie est la date actuelle qui utilise les conversions ISO ou bien 1899-12-30 qui utilise les conversions OLE.  
  
-   Si aucun fuseau horaire n'est fourni dans le type de données que le client utilise mais si le serveur peut stocker le fuseau, les données du client sont supposées apparaître dans le fuseau horaire du client.  
  
-   Si aucun fuseau horaire n'est fourni au serveur mais le client dispose d'informations sur les fuseaux, le fuseau horaire UTC est adopté. Ce comportement diffère de celui du serveur.  
  
-   Si l'heure est fournie mais le récepteur ne peut pas la stocker, le composant heure est ignoré.  
  
-   Si la date est fournie mais le récepteur ne peut pas la stocker, le composant date est ignoré.  
  
-   En cas de troncation des secondes ou des fractions de seconde lors de la conversion du client au serveur, DB_E_ERRORSOCCURRED est retourné et l'état DBSTATUS_E_DATAOVERFLOW est défini.  
  
-   En cas de troncation des secondes ou des fractions de seconde lors de la conversion du serveur au client, DBSTATUS_S_TRUNCATED est défini  
  
## <a name="in-this-section"></a>Dans cette section  
 [Conversions de client à serveur](../../oledb/ole-db-date-time/conversions-performed-from-client-to-server.md)  
 Décrit les conversions de date et d’heure effectuées entre une application cliente écrite avec le pilote OLE DB pour SQL Server et [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (ou ultérieur).  
  
 [Conversions de serveur à client](../../oledb/ole-db-date-time/conversions-performed-from-server-to-client.md)  
 Décrit les conversions de date/heure effectuées entre [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (ou ultérieur) et une application cliente écrite avec le pilote OLE DB pour SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Améliorations des types de données de date et d’heure &#40;OLE DB&#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
