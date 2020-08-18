---
description: Pilote ODBC pour Oracle
title: Pilote ODBC pour Oracle | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC]
- ODBC driver for Oracle [ODBC], about ODBC driver for Oracle
- Oracle data access [ODBC]
ms.assetid: 937e0662-8b1d-44f7-b077-4015c6605b2c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a561539ff960dfa6691d26496b1b62d2ee8ae763
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88449331"
---
# <a name="odbc-driver-for-oracle"></a>Pilote ODBC pour Oracle
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Le pilote ODBC Microsoft® pour Oracle vous permet de connecter votre application compatible ODBC à une base de données Oracle. Le pilote ODBC pour Oracle est conforme à la spécification Open Database Connectivity (ODBC) décrite dans le *Guide de référence du programmeur ODBC*. Il permet d’accéder aux packages PL/SQL, à l’intégration XA/DTC et à l’accès Oracle à partir de Internet Information Services (IIS).  
  
 Oracle RDBMS est un système de gestion de base de données relationnelle multi-utilisateur qui s’exécute avec différents systèmes d’exploitation de station de travail et de mini-ordinateurs. Les ordinateurs compatibles IBM exécutant Microsoft Windows peuvent communiquer avec les serveurs de base de données Oracle sur un réseau. Les réseaux pris en charge incluent Microsoft LAN Manager, NetWare, VINEs, DECnet et tout réseau qui prend en charge TCP/IP.  
  
 Le pilote ODBC pour Oracle permet à une application d’accéder aux données d’une base de données Oracle par le biais de l’interface ODBC. Le pilote peut accéder aux bases de données Oracle locales ou peut communiquer avec le réseau par le biais de SQL * Net. Le diagramme suivant détaille cette architecture d’application et de pilote.  
  
 ![Architecture du pilote ODBC Driver for Oracle app&#47;](../../odbc/microsoft/media/orcdrvsdkarch.gif "OrcDrvSDKArch")  
  
 Le pilote ODBC pour Oracle est conforme au niveau de conformité de l’API 1 et au niveau de conformité SQL. Il prend également en charge certaines fonctions du niveau de conformité de l’API 2 et la plus grande partie de la grammaire dans les niveaux de conformité SQL de base et étendu. Le pilote est compatible ODBC 2,5 et prend en charge les systèmes 32 bits. Oracle 7.3 x est entièrement pris en charge ; Oracle8 a une prise en charge limitée. Le pilote ODBC pour Oracle ne prend pas en charge les nouveaux types de données Oracle8 (types de données Unicode, objets BLOB, objets CLOB, etc.). il ne prend pas non plus en charge le nouveau modèle d’objet relationnel d’Oracle. Pour plus d’informations sur les types de données pris en charge, consultez [types de données pris en charge](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md) dans ce guide.  
  
 Pour accéder aux données Oracle, les composants suivants sont requis :  
  
-   Pilote ODBC pour Oracle  
  
-   Une base de données de SGBDR Oracle  
  
-   Logiciel client Oracle  
  
 En outre, pour les connexions distantes :  
  
-   Un réseau qui connecte les ordinateurs qui exécutent le pilote et la base de données. Le réseau doit prendre en charge les connexions SQL * Net.  
  
## <a name="component-documentation"></a>Documentation du composant  
 Ce guide contient des informations détaillées sur la configuration et la configuration du pilote Microsoft ODBC pour Oracle et sur l’ajout de fonctionnalités de programmation. Il contient également des documents de référence techniques.  
  
 Pour plus d’informations sur le comportement spécifique d’un produit Oracle, consultez la documentation qui accompagne le produit Oracle.  
  
 Pour plus d’informations sur la configuration ou la configuration du pilote Microsoft ODBC pour Oracle à l’aide de l’administrateur de la source de données ODBC, consultez la documentation de l' [administrateur de sources de données ODBC](../../odbc/admin/odbc-data-source-administrator.md) .  
  
 Cette section contient les rubriques suivantes :  
  
-   [Guide de l’utilisateur du pilote ODBC pour Oracle](../../odbc/microsoft/odbc-driver-for-oracle-user-s-guide.md)  
  
-   [Informations de référence du programmeur du pilote ODBC pour Oracle](../../odbc/microsoft/odbc-driver-for-oracle-programmer-s-reference.md)
