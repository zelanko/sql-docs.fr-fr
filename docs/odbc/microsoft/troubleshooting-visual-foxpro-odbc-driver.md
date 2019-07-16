---
title: Résolution des problèmes (pilote ODBC de Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- set ANSI [ODBC]
- troubleshooting Visual FoxPro ODBC driver [ODBC]
- remote views [ODBC]
- multitiered views [ODBC]
- parameterized views [ODBC], Visual FoxPro ODBC driver
- fetches [ODBC], Visual FoxPro ODBC driver
- positioned updates [ODBC]
- background fetching [ODBC]
ms.assetid: fd478dd8-666a-4f0a-a2d6-b94e81cbbe4b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4eeb6210b9bce124e16a1b4e666dee03c1d992be
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67912387"
---
# <a name="troubleshooting-visual-foxpro-odbc-driver"></a>Résolution des problèmes (pilote ODBC Visual FoxPro)
Les sections suivantes expliquent comment améliorer les performances et résoudre les problèmes que vous pouvez rencontrer lors de l’utilisation du pilote ODBC Visual FoxPro.  
  
## <a name="accessing-parameterized-views"></a>L’accès à des vues paramétrées  
 Vous ne pouvez pas accéder à des vues paramétrées dans une base de données Visual FoxPro à l’aide du pilote. Une vue paramétrable crée une clause WHERE dans SQL la vue **sélectionnez** instruction qui limite les enregistrements téléchargés sur les enregistrements qui remplissent les conditions de la clause WHERE créée à l’aide de la valeur fournie pour le paramètre. Étant donné que le pilote ne prend pas en charge la transmission de paramètres à la vue, tente d’accéder à une vue paramétrée en utilisant le pilote échoue.  
  
 La valeur du paramètre peut être fournie au moment de l’exécution ou passée par programmation à la vue.  
  
## <a name="accessing-remote-views"></a>L’accès à des vues distantes  
 Impossible d’accéder à distance vues dans une base de données Visual FoxPro à l’aide du pilote. Les affichages à distance pour accéder, les données non FoxPro ou une combinaison de FoxPro et les données non FoxPro. Pour accéder à des vues à distance, utilisez Visual FoxPro.  
  
## <a name="deleting-records"></a>Suppression d’enregistrements  
 Vous pouvez marquer des enregistrements marqués en suppression à l’aide du pilote, mais vous ne pouvez pas supprimer définitivement les enregistrements à partir de la base de données. Pour supprimer définitivement les enregistrements d’une table, utilisez Visual FoxPro.  
  
## <a name="increasing-performance-using-background-fetching"></a>Augmentation des performances à l’aide de l’extraction en arrière-plan  
 Vous pouvez améliorer les performances des extractions volumineuses à l’aide de l’arrière-plan de l’extraction de fonctionnalités du pilote. L’extraction en arrière-plan utilise un thread distinct pour extraire les données demandées à partir d’une source de données spécifique.  
  
 Vous pouvez employer l’arrière-plan de l’extraction pour une source de données dans une des manières suivantes :  
  
-   Vérifier le **extraire les données en arrière-plan** case à cocher sur la [boîte de dialogue d’installation de ODBC Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md).  
  
-   Utilisez le mot clé d’attribut BackgroundFetch dans votre chaîne de connexion.  
  
 Pour plus d’informations sur les mots clés attribut de chaîne de connexion, consultez [à l’aide de chaînes de connexion](../../odbc/microsoft/using-connection-strings.md).  
  
## <a name="updating-multitiered-views"></a>La mise à jour des vues de plusieurs niveaux  
 Une vue de plusieurs niveaux est une vue basée sur une ou plusieurs vues plutôt que sur une table de base. Lorsque vous mettez à jour des données dans une vue de plusieurs niveaux, les mises à jour s’arrêtent qu’un seul niveau, à la vue sur laquelle repose la vue de niveau supérieur ; tables de base ne sont pas mis à jour.  
  
## <a name="using-data-definition-language-ddl-in-stored-procedures"></a>À l’aide du langage de définition de données (DDL) dans les procédures stockées  
 Vous ne pouvez pas utiliser DDL, telles que CREATE TABLE ou ALTER TABLE, dans les procédures stockées de Visual FoxPro.  
  
 Pour plus d’informations sur le langage que vous pouvez utiliser dans les procédures stockées, consultez [prise en charge des règles, les déclencheurs, les valeurs par défaut et les procédures stockées](../../odbc/microsoft/support-rules-triggers-defaults-stored-procedures-visual-foxpro-odbc-driver.md).  
  
## <a name="using-positioned-updates"></a>À l’aide de mises à jour positionnées  
 Le pilote ne prend pas en charge les mises à jour positionnées. Utilisez la clause SQL WHERE pour identifier les lignes que vous souhaitez mettre à jour.  
  
## <a name="using-the-set-ansi-command"></a>À l’aide de la commande de ANSI SET  
 Si vous êtes un développeur Visual FoxPro, sachez que le paramètre par défaut pour SET ANSI est activé pour le pilote, contrairement au paramètre par défaut est désactivée (OFF) pour Visual FoxPro. La valeur par défaut sur le paramètre de SET ANSI permet à des sources de données Visual FoxPro à un comportement cohérent avec d’autres sources de données ODBC que généralement effectuent des comparaisons exactes. Vous pouvez modifier le paramètre par défaut. Pour plus d’informations, consultez [SET ANSI](../../odbc/microsoft/set-ansi-command.md).
