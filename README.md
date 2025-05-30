# ControlPro
Control Reparaciones Gama
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Control de Reparaciones Pro</title>
    <style>
        :root {
            --primary-color: #667eea;
            --secondary-color: #764ba2;
            --success-color: #56ab2f;
            --warning-color: #f093fb;
            --danger-color: #ff6b6b;
            --info-color: #74b9ff;
            --text-color: #2c3e50;
            --bg-color: #ffffff;
            --card-bg: #ffffff;
            --border-color: #e9ecef;
            --shadow: 0 2px 10px rgba(0,0,0,0.1);
            --gradient-bg: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }

        [data-theme="dark"] {
            --text-color: #e2e8f0;
            --bg-color: #1a202c;
            --card-bg: #2d3748;
            --border-color: #4a5568;
            --shadow: 0 2px 10px rgba(0,0,0,0.3);
            --gradient-bg: linear-gradient(135deg, #4a5568 0%, #2d3748 100%);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            /* Prevenir zoom en inputs en iOS */
            -webkit-text-size-adjust: 100%;
            -ms-text-size-adjust: 100%;
            text-size-adjust: 100%;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            font-size: 16px; /* Tamaño base estándar */
            line-height: 1.5;
            background: var(--gradient-bg);
            min-height: 100vh;
            padding: 8px;
            color: var(--text-color);
            transition: all 0.3s ease;
            /* Prevenir zoom en orientación */
            -webkit-text-size-adjust: none;
        }

        .container {
            max-width: 100%;
            margin: 0 auto;
            background: var(--bg-color);
            border-radius: 12px;
            box-shadow: var(--shadow);
            overflow: hidden;
            animation: slideIn 0.5s ease-out;
        }

        @keyframes slideIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        .header {
            background: linear-gradient(135deg, #ff6b6b, #ee5a24);
            color: white;
            padding: 16px;
            text-align: center;
            position: relative;
        }

        .header-controls {
            position: absolute;
            top: 16px;
            right: 16px;
            display: flex;
            gap: 8px;
        }

        .theme-toggle {
            background: rgba(255,255,255,0.2);
            border: none;
            color: white;
            padding: 8px 12px;
            border-radius: 20px;
            cursor: pointer;
            transition: all 0.3s;
            font-size: 14px;
            min-height: 44px; /* Tamaño mínimo táctil */
            min-width: 44px;
        }

        .theme-toggle:hover {
            background: rgba(255,255,255,0.3);
            transform: scale(1.1);
        }

        .offline-indicator {
            background: #ff6b6b;
            color: white;
            padding: 6px 12px;
            border-radius: 15px;
            font-size: 12px;
            display: none;
        }

        .logo {
            width: 50px;
            height: 50px;
            margin: 0 auto 8px;
            background: rgba(255,255,255,0.2);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            animation: pulse 2s infinite;
        }

        .header h1 {
            font-size: 20px;
            margin-bottom: 4px;
            font-weight: 600;
        }

        .header p {
            opacity: 0.9;
            font-size: 14px;
        }

        .main-content {
            padding: 16px;
        }

        .form-section {
            background: var(--card-bg);
            padding: 16px;
            border-radius: 10px;
            margin-bottom: 16px;
            border: 1px solid var(--border-color);
            animation: fadeIn 0.5s ease-out;
        }

        .form-section h2 {
            color: var(--text-color);
            margin-bottom: 12px;
            font-size: 18px;
            font-weight: 600;
        }

        .form-group {
            margin-bottom: 16px;
        }

        .form-group label {
            display: block;
            margin-bottom: 6px;
            color: var(--text-color);
            font-weight: 500;
            font-size: 14px;
        }

        .form-group input,
        .form-group textarea,
        .form-group select {
            width: 100%;
            padding: 12px;
            border: 1px solid var(--border-color);
            border-radius: 8px;
            font-size: 16px; /* Previene zoom en iOS */
            transition: all 0.3s;
            background: var(--card-bg);
            color: var(--text-color);
            min-height: 44px; /* Tamaño mínimo táctil */
            -webkit-appearance: none;
            appearance: none;
        }

        .form-group input:focus,
        .form-group textarea:focus,
        .form-group select:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 0 2px rgba(102, 126, 234, 0.2);
        }

        .form-group textarea {
            min-height: 80px;
            resize: vertical;
            font-family: inherit;
        }

        .form-row {
            display: grid;
            grid-template-columns: 1fr;
            gap: 16px;
        }

        .image-upload {
            border: 2px dashed var(--border-color);
            padding: 20px;
            text-align: center;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s;
            min-height: 80px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }

        .image-upload:hover {
            border-color: var(--primary-color);
            background: rgba(102, 126, 234, 0.1);
        }

        .image-upload p {
            font-size: 14px;
            margin: 4px 0;
        }

        .image-preview {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-top: 12px;
        }

        .image-item {
            position: relative;
            width: 80px;
            height: 80px;
            border-radius: 8px;
            overflow: hidden;
        }

        .image-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .image-remove {
            position: absolute;
            top: 4px;
            right: 4px;
            background: #ff6b6b;
            color: white;
            border: none;
            border-radius: 50%;
            width: 24px;
            height: 24px;
            cursor: pointer;
            font-size: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .btn {
            padding: 12px 16px;
            border: none;
            border-radius: 8px;
            font-size: 14px;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s;
            margin: 4px;
            min-height: 44px; /* Tamaño mínimo táctil */
            display: inline-flex;
            align-items: center;
            justify-content: center;
            text-decoration: none;
        }

        .btn:hover {
            transform: translateY(-1px);
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            color: white;
        }

        .btn-success {
            background: linear-gradient(135deg, var(--success-color), #a8e6cf);
            color: white;
        }

        .btn-warning {
            background: linear-gradient(135deg, var(--warning-color), #f5576c);
            color: white;
        }

        .btn-danger {
            background: linear-gradient(135deg, var(--danger-color), #ee5a24);
            color: white;
        }

        .btn-secondary {
            background: linear-gradient(135deg, var(--info-color), #0984e3);
            color: white;
        }

        .button-group {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
        }

        /* Filtros y búsqueda */
        .search-filters {
            display: grid;
            grid-template-columns: 1fr;
            gap: 12px;
            margin-bottom: 16px;
        }

        .search-box {
            position: relative;
        }

        .search-box input {
            padding-left: 40px;
        }

        .search-box::before {
            content: "🔍";
            position: absolute;
            left: 12px;
            top: 50%;
            transform: translateY(-50%);
            z-index: 1;
            font-size: 14px;
        }

        /* Paginación */
        .pagination {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 8px;
            margin: 16px 0;
            flex-wrap: wrap;
        }

        .pagination button {
            padding: 8px 12px;
            border: 1px solid var(--border-color);
            background: var(--card-bg);
            color: var(--text-color);
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.3s;
            min-height: 36px;
            font-size: 14px;
        }

        .pagination button:hover {
            background: var(--primary-color);
            color: white;
        }

        .pagination button.active {
            background: var(--primary-color);
            color: white;
        }

        .pagination button:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }

        .pagination span {
            font-size: 14px;
            color: var(--text-color);
            padding: 0 8px;
        }

        /* Lista de reparaciones */
        .repair-list {
            margin-top: 16px;
        }

        .repair-item {
            background: var(--card-bg);
            border: 1px solid var(--border-color);
            border-radius: 10px;
            padding: 16px;
            margin-bottom: 12px;
            box-shadow: var(--shadow);
            transition: all 0.3s;
            animation: fadeIn 0.5s ease-out;
        }

        .repair-item:hover {
            transform: translateY(-1px);
            box-shadow: 0 4px 15px rgba(0,0,0,0.12);
        }

        .repair-header {
            display: flex;
            justify-content: space-between;
            align-items: flex-start;
            margin-bottom: 12px;
            flex-wrap: wrap;
            gap: 8px;
        }

        .repair-title {
            font-weight: 600;
            color: var(--text-color);
            font-size: 16px;
            flex: 1;
            min-width: 200px;
        }

        .repair-cost {
            color: var(--success-color);
            font-weight: 600;
            font-size: 16px;
            white-space: nowrap;
        }

        .repair-details {
            color: var(--text-color);
            line-height: 1.6;
            opacity: 0.9;
            font-size: 14px;
        }

        .repair-details p {
            margin-bottom: 6px;
        }

        .repair-details strong {
            font-weight: 600;
        }

        .repair-actions {
            margin-top: 12px;
            display: flex;
            gap: 8px;
            flex-wrap: wrap;
        }

        .repair-actions .btn {
            margin: 0;
            font-size: 13px;
            padding: 8px 12px;
        }

        .repair-images {
            display: flex;
            gap: 8px;
            margin-top: 12px;
            flex-wrap: wrap;
        }

        .repair-images img {
            width: 60px;
            height: 60px;
            border-radius: 5px;
            object-fit: cover;
            cursor: pointer;
            transition: all 0.3s;
        }

        .repair-images img:hover {
            transform: scale(1.05);
        }

        .empty-state {
            text-align: center;
            padding: 32px 16px;
            color: var(--text-color);
            opacity: 0.7;
        }

        .empty-state svg {
            width: 64px;
            height: 64px;
            margin-bottom: 16px;
            opacity: 0.5;
        }

        .empty-state p {
            font-size: 14px;
            line-height: 1.5;
        }

        .status-badge {
            display: inline-block;
            padding: 4px 8px;
            border-radius: 12px;
            font-size: 11px;
            font-weight: 500;
            margin-left: 8px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .status-pendiente {
            background: #fff3cd;
            color: #856404;
        }

        .status-en-proceso {
            background: #d4edda;
            color: #155724;
        }

        .status-completado {
            background: #d1ecf1;
            color: #0c5460;
        }

        /* Notificaciones */
        .notification {
            position: fixed;
            top: 16px;
            right: 16px;
            padding: 12px 16px;
            border-radius: 8px;
            color: white;
            font-weight: 500;
            z-index: 9999;
            animation: slideInRight 0.3s ease-out;
            max-width: 280px;
            font-size: 14px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.3);
        }

        @keyframes slideInRight {
            from { transform: translateX(100%); opacity: 0; }
            to { transform: translateX(0); opacity: 1; }
        }

        .notification.success {
            background: var(--success-color);
        }

        .notification.error {
            background: var(--danger-color);
        }

        .notification.info {
            background: var(--info-color);
        }

        /* Modal para calendario */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.6);
            z-index: 10000;
            animation: fadeIn 0.3s ease-out;
            padding: 16px;
            overflow-y: auto;
        }

        .modal-content {
            position: relative;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: var(--card-bg);
            padding: 24px;
            border-radius: 12px;
            max-width: 500px;
            width: 100%;
            max-height: 80vh;
            overflow-y: auto;
            animation: slideIn 0.3s ease-out;
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 16px;
            padding-bottom: 12px;
            border-bottom: 1px solid var(--border-color);
        }

        .modal-header h2 {
            font-size: 18px;
            margin: 0;
        }

        .modal-close {
            background: none;
            border: none;
            font-size: 24px;
            cursor: pointer;
            color: var(--text-color);
            width: 32px;
            height: 32px;
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 4px;
        }

        .modal-close:hover {
            background: var(--border-color);
        }

        /* Responsive - Específico para móviles */
        @media (max-width: 768px) {
            body {
                padding: 4px;
                font-size: 16px; /* Mantener tamaño estándar */
            }

            .container {
                border-radius: 8px;
            }

            .header {
                padding: 12px;
            }

            .header h1 {
                font-size: 18px;
            }

            .header p {
                font-size: 13px;
            }

            .main-content {
                padding: 12px;
            }

            .form-section {
                padding: 12px;
                margin-bottom: 12px;
            }

            .form-row {
                grid-template-columns: 1fr;
            }
            
            .search-filters {
                grid-template-columns: 1fr;
            }
            
            .button-group {
                justify-content: center;
            }
            
            .repair-actions {
                flex-direction: column;
            }

            .repair-actions .btn {
                width: 100%;
                justify-content: center;
            }

            .header-controls {
                position: relative;
                top: auto;
                right: auto;
                justify-content: center;
                margin-top: 12px;
            }

            .repair-header {
                flex-direction: column;
                align-items: flex-start;
            }

            .repair-title {
                min-width: auto;
                margin-bottom: 4px;
            }

            .modal-content {
                margin: 16px;
                width: calc(100% - 32px);
                top: auto;
                left: auto;
                transform: none;
                position: relative;
            }

            .notification {
                right: 8px;
                left: 8px;
                max-width: none;
            }
        }

        /* Tablets */
        @media (min-width: 769px) and (max-width: 1024px) {
            .form-row {
                grid-template-columns: 1fr 1fr;
            }

            .search-filters {
                grid-template-columns: 2fr 1fr;
            }
        }

        /* Desktop */
        @media (min-width: 1025px) {
            .container {
                max-width: 1200px;
            }

            .form-row {
                grid-template-columns: 1fr 1fr;
            }

            .search-filters {
                grid-template-columns: 2fr 1fr 1fr 1fr;
            }
        }

        .hidden {
            display: none;
        }

        /* Indicador de entrega próxima */
        .delivery-warning {
            background: linear-gradient(135deg, #ffa726, #ff7043);
            color: white;
            padding: 4px 8px;
            border-radius: 12px;
            font-size: 11px;
            margin-left: 8px;
            animation: pulse 1.5s infinite;
            display: inline-block;
        }

        /* Ajustes específicos para prevenir zoom */
        input[type="search"],
        input[type="text"],
        input[type="email"],
        input[type="tel"],
        input[type="number"],
        input[type="date"],
        textarea,
        select {
            font-size: 16px !important; /* Previene zoom en iOS */
        }

        /* Mejoras de accesibilidad táctil */
        button, .btn, input[type="button"], input[type="submit"] {
            min-height: 44px;
            min-width: 44px;
        }

        /* Prevenir selección de texto en botones */
        .btn, button {
            -webkit-user-select: none;
            -moz-user-select: none;
            -ms-user-select: none;
            user-select: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <div class="header-controls">
                <button class="theme-toggle" onclick="toggleTheme()" aria-label="Cambiar tema">🌙</button>
                <div class="offline-indicator" id="offline-indicator">Sin conexión</div>
            </div>
            <div class="logo">🔧</div>
            <h1>Control de Reparaciones Pro</h1>
            <p>Gestiona tus servicios de reparación con estilo</p>
        </div>

        <div class="main-content">
            <!-- Formulario -->
            <div class="form-section">
                <h2 id="form-title">Agregar Nueva Reparación</h2>
                <form id="repair-form">
                    <div class="form-row">
                        <div class="form-group">
                            <label for="cliente">Nombre del Cliente</label>
                            <input type="text" id="cliente" name="cliente" required>
                        </div>
                        <div class="form-group">
                            <label for="contacto">Contacto</label>
                            <input type="text" id="contacto" name="contacto" placeholder="Teléfono o email">
                        </div>
                    </div>
                    
                    <div class="form-row">
                        <div class="form-group">
                            <label for="modelo">Modelo/Equipo</label>
                            <input type="text" id="modelo" name="modelo" required>
                        </div>
                        <div class="form-group">
                            <label for="costo">Costo ($)</label>
                            <input type="number" id="costo" name="costo" step="0.01" min="0">
                        </div>
                    </div>

                    <div class="form-row">
                        <div class="form-group">
                            <label for="reparacion">Tipo de Reparación</label>
                            <input type="text" id="reparacion" name="reparacion" required>
                        </div>
                        <div class="form-group">
                            <label for="estado">Estado</label>
                            <select id="estado" name="estado">
                                <option value="pendiente">Pendiente</option>
                                <option value="en-proceso">En Proceso</option>  
                                <option value="completado">Completado</option>
                            </select>
                        </div>
                    </div>

                    <div class="form-row">
                        <div class="form-group">
                            <label for="fechaEntrega">Fecha de Entrega</label>
                            <input type="date" id="fechaEntrega" name="fechaEntrega">
                        </div>
                        <div class="form-group">
                            <label for="prioridad">Prioridad</label>
                            <select id="prioridad" name="prioridad">
                                <option value="baja">Baja</option>
                                <option value="media">Media</option>
                                <option value="alta">Alta</option>
                                <option value="urgente">Urgente</option>
                            </select>
                        </div>
                    </div>

                    <div class="form-group">
                        <label for="observaciones">Observaciones</label>
                        <textarea id="observaciones" name="observaciones" placeholder="Detalles adicionales, problemas encontrados, etc."></textarea>
                    </div>

                    <div class="form-group">
                        <label>Imágenes del Equipo/Problema</label>
                        <div class="image-upload" onclick="document.getElementById('image-input').click()">
                            <p>📷 Haz clic para adjuntar imágenes</p>
                            <p style="font-size: 12px; opacity: 0.7;">Máximo 5 imágenes por reparación</p>
                        </div>
                        <input type="file" id="image-input" multiple accept="image/*" style="display: none;" onchange="handleImageUpload(event)">
                        <div class="image-preview" id="image-preview"></div>
                    </div>

                    <div class="button-group">
                        <button type="submit" class="btn btn-primary">
                            <span id="btn-text">Guardar Reparación</span>
                        </button>
                        <button type="button" class="btn btn-secondary" id="btn-cancel" onclick="cancelEdit()" style="display: none;">
                            Cancelar
                        </button>
                    </div>
                </form>
            </div>

            <!-- Botones de Acción -->
            <div class="form-section">
                <h2>Acciones</h2>
                <div class="button-group">
                    <button class="btn btn-success" onclick="exportData()">
                        📥 Hacer Copia de Seguridad
                    </button>
                    <button class="btn btn-warning" onclick="importData()">
                        📤 Restaurar Copia
                    </button>
                    <button class="btn btn-secondary" onclick="showCalendar()">
                        📅 Calendario de Entregas
                    </button>
                    <button class="btn btn-danger" onclick="clearAllData()">
                        🗑 Borrar Todo
                    </button>
                </div>
                <input type="file" id="file-input" accept=".json" style="display: none;" onchange="handleFileImport(event)">
            </div>

            <!-- Filtros y Búsqueda -->
            <div class="form-section">
                <h2>Filtros y Búsqueda</h2>
                <div class="search-filters">
                    <div class="search-box">
                        <input type="text" id="search-term" placeholder="Buscar por cliente, modelo o reparación..." onkeyup="filterRepairs()">
                    </div>
                    <div class="form-group">
                        <select id="status-filter" onchange="filterRepairs()">
                            <option value="">Todos los estados</option>
                            <option value="pendiente">Pendiente</option>
                            <option value="en-proceso">En Proceso</option>
                            <option value="completado">Completado</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <select id="sort-by" onchange="sortRepairs()">
                            <option value="fecha-desc">Fecha (Más reciente)</option>
                            <option value="fecha-asc">Fecha (Más antigua)</option>
                            <option value="cliente-asc">Cliente (A-Z)</option>
                            <option value="cliente-desc">Cliente (Z-A)</option>
                            <option value="costo-desc">Costo (Mayor)</option>
                            <option value="costo-asc">Costo (Menor)</option>
                            <option value="entrega-asc">Entrega próxima</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <select id="items-per-page" onchange="updatePagination()">
                            <option value="5">5 por página</option>
                            <option value="10" selected>10 por página</option>
                            <option value="20">20 por página</option>
                            <option value="50">50 por página</option>
                        </select>
                    </div>
                </div>
            </div>

            <!-- Lista de Reparaciones -->
            <div class="repair-list">
                <h2>Reparaciones Registradas</h2>
                <div class="pagination" id="pagination-top"></div>
                <div id="repairs-container">
                    <div class="empty-state">
                        <svg viewBox="0 0 24 24" fill="currentColor">
                            <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/>
                        </svg>
                        <p>No hay reparaciones registradas aún.<br>Agrega tu primera reparación usando el formulario de arriba.</p>
