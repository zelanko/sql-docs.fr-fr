---
title: Liaisons et conversions (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB]
- bindings [OLE DB]
- OLE DB, bindings and conversions
ms.assetid: c187df58-a8c8-4c74-a76f-663abbc5f0c1
author: rothja
ms.author: jroth
ms.openlocfilehash: 140be806cfb79996c68b7c413c7998fcc0c20ebe
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85043880"
---
# <a name="bindings-and-conversions-ole-db"></a>Liaisons et conversions (OLE DB)
  Cette section explique comment réaliser des conversions entre des valeurs `datetime` et `datetimeoffset`. Les conversions décrites dans cette section sont soit déjà fournies par OLE DB, soit une extension cohérente de ce dernier.  
  
 Le format des littéraux et des chaînes pour les dates et les heures dans OLE DB suit généralement la norme ISO et ne dépend pas des paramètres régionaux du client. Une exception est DBTYPE_DATE où la norme est OLE Automation. Toutefois, du fait que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client effectue uniquement des conversions entre des types lorsque des données sont transmises vers ou depuis le client, il n'existe aucun moyen de contraindre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client à effectuer des conversions entre DBTYPE_DATE et un format de chaîne. Sinon, les chaînes utilisent les formats suivants (le texte entre crochets indique un élément facultatif) :  
  
-   Le format des chaînes `datetime` et `datetimeoffset` est le suivant :  
  
     *aaaa* - *mm* - *JJ*[ *hh*:*mm*:*SS*[.* 9999999*] [ ?? *hh*:*mm*]]  
  
-   Le format des chaînes `time` est le suivant :  
  
     *hh*:*mm*:*ss*[.*9999999*]  
  
-   Le format des chaînes `date` est le suivant :  
  
     *aaaa*-*mm*-*jj*  
  
> [!NOTE]  
>  Les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client et SQLOLEDB autorisaient l'implémentation de conversions OLE en cas d'échec des processus de conversion standard. C'est pourquoi certaines conversions réalisées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 et versions ultérieures diffèrent de la spécification OLE DB.  
  
 Les conversions de chaînes autorisent une souplesse en matière d'espace et de largeur de champ. Pour plus d’informations, consultez la section « formats de données : chaînes et littéraux » dans [type de données prise en charge de OLE DB améliorations de la date et](data-type-support-for-ole-db-date-and-time-improvements.md)de l’heure.  
  
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
 [Conversions de client à serveur](conversions-performed-from-client-to-server.md)  
 Décrit les conversions date/heure effectuées entre une application cliente écrite avec le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client et [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (ou version ultérieure).  
  
 [Conversions de serveur à client](conversions-performed-from-server-to-client.md)  
 Décrit les conversions date/heure effectuées entre [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (ou version ultérieure) et une application cliente écrite avec le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="see-also"></a>Voir aussi  
 [Améliorations des types de données de date et d’heure &#40;OLE DB&#41;](date-and-time-improvements-ole-db.md)  
  
  
