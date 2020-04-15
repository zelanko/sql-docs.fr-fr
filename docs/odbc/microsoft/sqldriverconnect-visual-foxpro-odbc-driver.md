---
title: SQLDriverConnect (Visual FoxPro ODBC Driver) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 10492c8f-3a18-4971-9db8-879e878083b9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5e270f8c9be42dc109adeaa49acb84f29f2b9511
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307090"
---
# <a name="sqldriverconnect-visual-foxpro-odbc-driver"></a>SQLDriverConnect (pilote ODBC Visual FoxPro)
> [!NOTE]  
>  Ce sujet contient des informations visuelles spécifiques à FoxPro ODBC Driver. Pour plus d’informations générales sur cette fonction, voir le sujet approprié sous [ODBC API Référence](../../odbc/reference/syntax/odbc-api-reference.md).  
  
 Soutien: Complet  
  
 Conformité API ODBC: Niveau 1  
  
 Se connecte à une source de données existante, qui peut être soit une [base de données](../../odbc/microsoft/visual-foxpro-terminology.md) ou un répertoire de tables [gratuites](../../odbc/microsoft/visual-foxpro-terminology.md). Les mots clés d’attribut ODBC UID et PWD sont ignorés. Le tableau suivant répertorie les mots clés d’attributs supportés supplémentaires.  
  
|Mot-clé d’attribut ODBC|Valeur d'attribut|  
|----------------------------|---------------------|  
|DSN||  
|Identificateur d’utilisateur|Ignoré par le visual FoxPro ODBC Driver, mais ne génère pas d’erreur.|  
|PWD|Ignoré par le visual FoxPro ODBC Driver, mais ne génère pas d’erreur.|  
|Pilote|Le nom et l’emplacement du Visual FoxPro ODBC Driver; mise en œuvre par le Driver Manager.|  
  
|Visual FoxPro ODBC Driver attribut mot-clé|Valeur d'attribut|  
|-------------------------------------------------|---------------------|  
|ContexteFetch|"Oui" ou "Non"|  
|Copies assemblées|"Machine" ou autre séquence de collation. Pour une liste de séquences de collation prises en charge, voir [SET COLLATE](../../odbc/microsoft/set-collate-command.md).|  
|Description||  
|Exclusif|"Oui" ou "Non"|  
|SourceDB|Un chemin entièrement qualifié vers un répertoire contenant zéro ou plus [de tables gratuites,](../../odbc/microsoft/visual-foxpro-terminology.md)ou le chemin absolu et le nom de fichier pour une [base de données](../../odbc/microsoft/visual-foxpro-terminology.md).|  
|SourceType|"DBC" ou "DBF"|  
|Version||  
  
 Si le nom de source de données n’est pas spécifié, le gestionnaire de pilote invite l’utilisateur pour les informations (selon le paramètre de l’argument de la *conformité fDriver)* et continue ensuite. Si plus d’informations sont nécessaires, le visual FoxPro ODBC Driver affiche le dialogue rapide.  
  
 Pour plus d’informations, voir [SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md) dans la *référence du programmeur ODBC*.
