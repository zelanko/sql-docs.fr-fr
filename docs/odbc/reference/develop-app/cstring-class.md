---
title: Classe CString (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CString class [ODBC]
ms.assetid: 18630642-76fa-43c4-a154-3f0969ec9b50
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0f941061bf1bc7671d4744d309770fc92c95dd6e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301648"
---
# <a name="cstring-class"></a>CString, classe
Étant donné que les objets de la classe **CString** dans Microsoft® Visual C-® sont signés et que les arguments de chaîne dans les fonctions ODBC ne sont pas signés, les applications qui transmettent les objets **CString** aux fonctions ODBC sans les lancer recevront des avertissements de compilateur.
