---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4685d209d768bd3ff41c1c7367ef6cb6dcd45bcf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63043858"
---
# <a name="odbc-driver-for-oracle"></a>Pilote ODBC pour Oracle
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 Microsoft® ODBC Driver for Oracle vous permet de connecter votre application compatible ODBC à une base de données Oracle. Le pilote ODBC pour Oracle est conforme à la spécification Open Database Connectivity (ODBC) décrite dans la *de référence du programmeur ODBC*. Il autorise l’accès aux packages de PL/SQL, l’intégration de XA/DTC et accès Oracle à partir de dans Internet Information Services (IIS).  
  
 Oracle SGBDR est un système de gestion de base de données relationnelle multi-utilisateurs qui s’exécute avec différents systèmes d’exploitation de station de travail et ses. Ordinateurs compatibles IBM exécutant Microsoft Windows peuvent communiquer avec les serveurs de base de données Oracle sur un réseau. Réseaux pris en charge incluent Microsoft LAN Manager, NetWare, VINES, DECnet et n’importe quel réseau qui prend en charge de TCP/IP.  
  
 Le pilote ODBC pour Oracle permet à une application accéder aux données dans une base de données Oracle via l’interface ODBC. Le pilote peut accéder aux bases de données Oracle locales ou il peut communiquer avec le réseau via SQL * Net. Le diagramme suivant décrit en détail cette architecture de pilote et des applications.  
  
 ![Pilote ODBC pour Oracle application&#47;architecture du pilote](../../odbc/microsoft/media/orcdrvsdkarch.gif "OrcDrvSDKArch")  
  
 Le pilote ODBC pour Oracle est conforme à l’API de la conformité au niveau 1 et niveau de conformité SQL standard. Il prend également en charge certaines fonctions dans les API de la conformité au niveau 2 et la majeure partie de la grammaire dans les niveaux de conformité Core et SQL étendue. Le pilote est conforme à ODBC 2.5 et prend en charge les systèmes 32 bits. Oracle 7.3 x est pris en charge entièrement ; Oracle8 prend en charge limitée. Le pilote ODBC pour Oracle ne prend pas en charge des nouveaux types de données Oracle8 - Unicode des types de données, objets BLOB, CLOB et ainsi de suite - ni prend-elle en charge nouveau modèle d’Oracle d’objet relationnel. Pour plus d’informations sur les types de données pris en charge, consultez [pris en charge les Types de données](../../odbc/microsoft/supported-data-types-odbc-driver-for-oracle.md) dans ce guide.  
  
 Pour accéder aux données Oracle, les composants suivants sont requis :  
  
-   Le pilote ODBC pour Oracle  
  
-   Une base de données Oracle SGBDR  
  
-   Logiciel Client Oracle  
  
 En outre, pour les connexions à distance :  
  
-   Un réseau qui connecte les ordinateurs qui exécutent le pilote et la base de données. Le réseau doit prendre en charge SQL * Net de connexions.  
  
## <a name="component-documentation"></a>Documentation de composant  
 Ce guide contient des informations détaillées sur la configuration et de configuration du pilote ODBC de Microsoft pour Oracle et d’ajout de la fonctionnalité de programmation. Il contient également des documents de référence.  
  
 Pour plus d’informations concernant le comportement du produit Oracle spécifique, consultez la documentation qui accompagne le produit d’Oracle.  
  
 Pour plus d’informations sur la configuration ou la configuration du pilote ODBC de Microsoft pour Oracle à l’aide de l’administrateur de sources de données ODBC, consultez le [administrateur de sources de données ODBC](../../odbc/admin/odbc-data-source-administrator.md) documentation.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Guide de l’utilisateur du pilote ODBC pour Oracle](../../odbc/microsoft/odbc-driver-for-oracle-user-s-guide.md)  
  
-   [Informations de référence du programmeur du pilote ODBC pour Oracle](../../odbc/microsoft/odbc-driver-for-oracle-programmer-s-reference.md)
