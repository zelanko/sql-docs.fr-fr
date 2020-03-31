---
title: ODBC Driver pour Oracle (fr) Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2b5f1aabd23a587e681c33aed4b4119523444219
ms.sourcegitcommit: fc5b757bb27048a71bb39755648d5cefe25a8bc6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80402613"
---
# <a name="odbc-driver-for-oracle"></a>Pilote ODBC pour Oracle
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le [pilote ODBC fourni par Oracle](https://www.oracle.com/database/technologies/releasenote-odbc-ic.html).  
  
 Le pilote Microsoft® ODBC pour Oracle vous permet de connecter votre application conforme à l’ODBC à une base de données Oracle. Le pilote ODBC pour Oracle est conforme aux spécifications de connectivité open Database (ODBC) décrites dans la *référence du programmeur ODBC*. Il permet l’accès aux forfaits PL/SQL, à l’intégration XA/DTC et à l’accès Oracle à partir des services d’information Internet (IIS).  
  
 Oracle RDBMS est un système de gestion de base de données relationnel multiusique qui fonctionne avec divers systèmes d’exploitation de poste de travail et de mini-ordinateurs. Les ordinateurs compatibles AVEC IBM exécutant Microsoft Windows peuvent communiquer avec les serveurs de base de données Oracle sur un réseau. Les réseaux pris en charge comprennent Microsoft LAN Manager, NetWare, VINES, DECnet, et tout réseau qui prend en charge TCP / IP.  
  
 Le pilote ODBC pour Oracle permet à une application d’accéder aux données dans une base de données Oracle via l’interface ODBC. Le conducteur peut accéder aux bases de données Oracle locales ou il peut communiquer avec le réseau via SQL-Net. Le diagramme suivant détaille cette application et l’architecture du conducteur.  
  
 ![ODBC Driver pour l’application Oracle&#47;l’architecture du conducteur](../../odbc/microsoft/media/orcdrvsdkarch.gif "OrcDrvSDKArch")  
  
 Le pilote ODBC pour Oracle est conforme au niveau de conformité 1 et au noyau de niveau de conformité SQL de l’API. Il prend également en charge certaines fonctions dans le niveau de conformité API 2 et la plupart de la grammaire dans les niveaux de conformité sqL de base et étendus. Le conducteur est conforme à la conformité ODBC 2.5 et prend en charge les systèmes 32 bits. Oracle 7.3x est entièrement pris en charge; Oracle8 a un soutien limité. Le pilote ODBC pour Oracle ne prend en charge aucun des nouveaux types de données Oracle8 - types de données Unicode, BLOBs, CLOB, etc . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . Pour plus d’informations sur les types de données pris en charge, consultez [les types de données pris](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md) en charge dans ce guide.  
  
 Pour accéder aux données Oracle, les composants suivants sont nécessaires :  
  
-   Le pilote ODBC pour Oracle  
  
-   Une base de données Oracle RDBMS  
  
-   Logiciel Client Oracle  
  
 En outre, pour les connexions à distance:  
  
-   Un réseau qui connecte les ordinateurs qui exécutent le pilote et la base de données. Le réseau doit prendre en charge les connexions SQL-Net.  
  
## <a name="component-documentation"></a>Documentation des composants  
 Ce guide contient des informations détaillées sur la mise en place et la configuration du pilote Microsoft ODBC pour Oracle et l’ajout de fonctionnalités programmatiques. Il contient également du matériel de référence technique.  
  
 Pour plus d’informations sur le comportement spécifique du produit Oracle, consultez la documentation qui accompagne le produit Oracle.  
  
 Pour plus d’informations sur la configuration ou la configuration du pilote Microsoft ODBC pour Oracle à l’aide de l’administrateur de source de données ODBC, consultez la documentation [de l’administrateur de source de données ODBC.](../../odbc/admin/odbc-data-source-administrator.md)  
  
 Cette section contient les rubriques suivantes :  
  
-   [Guide de l’utilisateur du pilote ODBC pour Oracle](../../odbc/microsoft/odbc-driver-for-oracle-user-s-guide.md)  
  
-   [Informations de référence du programmeur du pilote ODBC pour Oracle](../../odbc/microsoft/odbc-driver-for-oracle-programmer-s-reference.md)
