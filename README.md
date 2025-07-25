<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Controle de Réus Presos - Versão Final</title>
    <link rel="preconnect" href="https://fonts.googleapis.com/">
    <link rel="preconnect" href="https://fonts.gstatic.com/" crossorigin="">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">
    <style>
        /* Base Variables - Fallback if no theme is active, or for common properties */
        :root {
            --font-family: 'Poppins', sans-serif;
            --shadow-color: rgba(0, 0, 0, 0.5);
            /* Define RGB components for dynamic transparency */
            --text-primary-rgb: 224, 224, 224; /* Default to dark theme's primary text */
            --theme-invert-filter: 1; /* Default to invert for dark theme date picker */
            --character-color: auto; /* Default, will be set by theme */
        }

        /* Dark Theme Variables */
        body.dark-theme {
            --bg-color: #121212;
            --surface-color: #1e1e1e;
            --primary-border-color: rgba(255, 255, 255, 0.1);
            --secondary-border-color: rgba(255, 255, 255, 0.2);
            --text-primary: #e0e0e0;
            --text-secondary: #a0a0a0;
            --accent-main: #00ff85; /* Green as main accent */
            --accent-secondary: #00e5ff; /* Cyan for other accents */
            --accent-contrast: #ff00e5; /* Magenta for contrast */
            --accent-warning: #ffd700; /* Gold for warning */
            --accent-error: #e53e3e; /* Red for error */
            --shadow-color: rgba(0, 0, 0, 0.5);
            
            --table-bg-odd: rgba(0, 0, 0, 0.15);
            --table-bg-even: rgba(0, 0, 0, 0.05);
            --table-header-bg: var(--bg-color);
            --table-header-text: white;
            --table-row-hover: var(--secondary-border-color);
            --table-border-bottom: 1px solid var(--primary-border-color);
            --table-header-border-bottom: 2px solid var(--accent-main); /* Green header border */
            --input-bg: #2a2a2a;
            --input-border: 1px solid var(--primary-border-color);
            --input-text: var(--text-primary);
            --text-primary-rgb: 224, 224, 224;
            --theme-invert-filter: 1;
            --character-color: var(--text-primary);

            --highlight-row-color: #ffd700; /* Gold */
            --complete-row-color: #00ff85; /* Green */
        }

        /* Light Theme Variables */
        body.light-theme {
            --bg-color: #f0f2f5; /* Very light gray */
            --surface-color: #ffffff; /* White */
            --primary-border-color: rgba(0, 0, 0, 0.08); /* Light, subtle border */
            --secondary-border-color: rgba(0, 0, 0, 0.15); /* Slightly darker for hover */
            --text-primary: #333333; /* Black text */
            --text-secondary: #666666; /* Medium gray text */
            --accent-main: #ffc107; /* Gold as main accent */
            --accent-secondary: #333333; /* Black for other accents */
            --accent-contrast: #6f42c1; /* Purple for contrast */
            --accent-green: #28a745; /* Green for success */
            --accent-warning: #ffc107; /* Yellow for warning (same as main) */
            --accent-error: #dc3545; /* Red for error */
            --shadow-color: rgba(0, 0, 0, 0.1);

            --table-bg-odd: rgba(255, 255, 255, 0.8);
            --table-bg-even: rgba(245, 245, 245, 0.9);
            --table-header-bg: #e9ecef;
            --table-header-text: var(--text-primary); /* Black header text */
            --table-row-hover: rgba(255, 255, 200, 0.6); /* Pale yellow hover */
            --table-border-bottom: 1px solid rgba(0, 0, 0, 0.05);
            --table-header-border-bottom: 2px solid var(--accent-main); /* Gold header border */
            --input-bg: #ffffff;
            --input-border: 1px solid rgba(0, 0, 0, 0.15);
            --input-text: var(--text-primary);
            --text-primary-rgb: 51, 51, 51; /* RGB for #333333 */
            --theme-invert-filter: 0;
            --character-color: var(--text-primary);

            --highlight-row-color: #ffc107; /* Yellow */
            --complete-row-color: #28a745; /* Green */
        }

        /* Gray Theme Variables (New) */
        body.gray-theme {
            --bg-color: #e0e0e0; /* Light gray */
            --surface-color: #f5f5f5; /* Lighter gray */
            --primary-border-color: rgba(0, 0, 0, 0.1);
            --secondary-border-color: rgba(0, 0, 0, 0.25);
            --text-primary: #424242; /* Dark gray text */
            --text-secondary: #757575; /* Medium gray text */
            --accent-main: #2196f3; /* Blue as main accent */
            --accent-secondary: #03a9f4; /* Light blue for other accents */
            --accent-contrast: #00bcd4; /* Cyan for contrast */
            --accent-green: #4caf50; /* Green for success */
            --accent-warning: #ffeb3b; /* Yellow for warning */
            --accent-error: #f44336; /* Red for error */
            --shadow-color: rgba(0, 0, 0, 0.15);

            --table-bg-odd: rgba(255, 255, 255, 0.9);
            --table-bg-even: rgba(240, 240, 240, 0.95);
            --table-header-bg: #bdbdbd;
            --table-header-text: #212121;
            --table-row-hover: rgba(173, 216, 230, 0.6); /* Light blue hover */
            --table-border-bottom: 1px solid rgba(0, 0, 0, 0.08);
            --table-header-border-bottom: 2px solid var(--accent-main); /* Blue header border */
            --input-bg: #ffffff;
            --input-border: 1px solid rgba(0, 0, 0, 0.15);
            --input-text: var(--text-primary);
            --text-primary-rgb: 66, 66, 66; /* RGB for #424242 */
            --theme-invert-filter: 0;
            --character-color: var(--text-primary);

            --highlight-row-color: #ffeb3b; /* Yellow */
            --complete-row-color: #4caf50; /* Green */
        }

        /* Futuristic Theme */
        body.futuristic-theme {
            --font-family: 'Arial', sans-serif;
            --bg-color: #0d0d1a;
            --surface-color: #1a1a33;
            --primary-border-color: rgba(70, 200, 255, 0.2);
            --secondary-border-color: rgba(70, 200, 255, 0.4);
            --text-primary: #e6f7ff;
            --text-secondary: #a0e6ff;
            --accent-main: #00e5ff; /* Electric Blue */
            --accent-secondary: #00ff85; /* Neon Green */
            --accent-contrast: #ff00e5; /* Neon Magenta */
            --accent-green: #00ff85; /* Neon Green */
            --accent-warning: #ffe500; /* Neon Yellow */
            --accent-error: #ff3366; /* Neon Red */
            --shadow-color: rgba(0, 229, 255, 0.3);

            --table-bg-odd: rgba(0, 229, 255, 0.05);
            --table-bg-even: rgba(0, 229, 255, 0.02);
            --table-header-bg: #1a1a33;
            --table-header-text: var(--accent-main);
            --table-row-hover: rgba(0, 229, 255, 0.15);
            --table-border-bottom: 1px solid var(--primary-border-color);
            --table-header-border-bottom: 2px solid var(--accent-contrast);
            --input-bg: #2a2a47;
            --input-border: 1px solid var(--secondary-border-color);
            --input-text: var(--text-primary);
            --text-primary-rgb: 230, 247, 255;
            --theme-invert-filter: 1;
            --character-color: var(--text-primary);

            --highlight-row-color: #ffe500; /* Neon Yellow */
            --complete-row-color: #00ff85; /* Neon Green */
        }

        /* Retro Theme */
        body.retro-theme {
            --font-family: 'Times New Roman', serif;
            --bg-color: #fdf6e3; /* Cream */
            --surface-color: #fdf6e3;
            --primary-border-color: #dcb387; /* Sepia Brown Light */
            --secondary-border-color: #b88b5e; /* Sepia Brown */
            --text-primary: #333333; /* Dark Brown */
            --text-secondary: #666666; /* Medium Brown */
            --accent-main: #a8201a; /* Rusty Red */
            --accent-secondary: #c98e21; /* Muted Gold */
            --accent-contrast: #3d3b8e; /* Muted Violet */
            --accent-green: #5c7457; /* Forest Green */
            --accent-warning: #e09f3e; /* Burnt Orange */
            --accent-error: #8b0000; /* Dark Red */
            --shadow-color: rgba(0, 0, 0, 0.2);

            --table-bg-odd: rgba(255, 255, 255, 0.7);
            --table-bg-even: rgba(245, 245, 245, 0.8);
            --table-header-bg: #dcb387;
            --table-header-text: #333333;
            --table-row-hover: rgba(220, 180, 140, 0.5);
            --table-border-bottom: 1px solid #dcb387;
            --table-header-border-bottom: 2px solid var(--accent-main);
            --input-bg: #fffbf0;
            --input-border: 1px solid #b88b5e;
            --input-text: var(--text-primary);
            --text-primary-rgb: 51, 51, 51;
            --theme-invert-filter: 0;
            --character-color: var(--text-primary);

            --highlight-row-color: #e09f3e; /* Burnt Orange */
            --complete-row-color: #5c7457; /* Forest Green */
        }

        /* Simple Theme */
        body.simple-theme {
            --font-family: 'Helvetica Neue', sans-serif;
            --bg-color: #f8f8f8;
            --surface-color: #ffffff;
            --primary-border-color: #e0e0e0;
            --secondary-border-color: #d0d0d0;
            --text-primary: #333333;
            --text-secondary: #777777;
            --accent-main: #3498db; /* Blue */
            --accent-secondary: #2ecc71; /* Green */
            --accent-contrast: #e74c3c; /* Red */
            --accent-green: #2ecc71; /* Green */
            --accent-warning: #f1c40f; /* Yellow */
            --accent-error: #e74c3c; /* Red */
            --shadow-color: rgba(0, 0, 0, 0.1);

            --table-bg-odd: rgba(245, 245, 245, 0.9);
            --table-bg-even: rgba(255, 255, 255, 0.95);
            --table-header-bg: #ececec;
            --table-header-text: var(--text-primary);
            --table-row-hover: rgba(52, 152, 219, 0.1);
            --table-border-bottom: 1px solid #f0f0f0;
            --table-header-border-bottom: 2px solid var(--accent-main);
            --input-bg: #ffffff;
            --input-border: 1px solid #dcdcdc;
            --input-text: var(--text-primary);
            --text-primary-rgb: 51, 51, 51;
            --theme-invert-filter: 0;
            --character-color: var(--text-primary);

            --highlight-row-color: #f1c40f; /* Yellow */
            --complete-row-color: #2ecc71; /* Green */
        }


        /* General styles */
        * {
            margin: 0; padding: 0; box-sizing: border-box;
        }

        body {
            font-family: var(--font-family);
            background: var(--bg-color);
            color: var(--text-primary);
            min-height: 100vh;
            padding: 20px;
            transition: background-color 0.5s ease, color 0.5s ease, font-family 0.5s ease;
        }
        
        .container {
            max-width: 95%; margin: 0 auto; background: var(--surface-color);
            border-radius: 20px; box-shadow: 0 20px 50px var(--shadow-color);
            border: 1px solid var(--primary-border-color);
            overflow: hidden; animation: fadeIn 1s ease-out;
            transition: background 0.5s ease, border-color 0.5s ease, box-shadow 0.5s ease;
        }

        @keyframes fadeIn { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }

        .header {
            padding: 40px; text-align: center; position: relative;
            background-color: rgba(30, 30, 30, 0.5); 
            backdrop-filter: blur(10px);
            border-bottom: 1px solid var(--primary-border-color);
            transition: background-color 0.5s ease, border-color 0.5s ease, backdrop-filter 0.5s ease;
        }
        .header h1 {
            font-size: 3em; font-weight: 700;
            background: -webkit-linear-gradient(45deg, var(--accent-main), var(--accent-contrast));
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
            transition: background 0.5s ease;
        }
        .header p { font-size: 1.2em; color: var(--text-secondary); margin-top: 10px; transition: color 0.5s ease; }
        
        .save-status {
            position: absolute; top: 20px; right: 20px; padding: 8px 15px;
            border-radius: 10px; font-size: 14px; font-weight: 500; transition: all 0.4s ease;
            background: var(--accent-green);
            color: black;
        }

        .tabs { display: flex; background: var(--bg-color); border-bottom: 1px solid var(--primary-border-color); transition: background 0.5s ease, border-color 0.5s ease; }
        .tab {
            flex: 1; padding: 18px 20px; background: transparent; border: none;
            cursor: pointer; font-size: 16px; font-weight: 600; color: var(--text-secondary);
            transition: all 0.3s ease; border-bottom: 4px solid transparent; position: relative;
        }
        .tab:hover { color: var(--text-primary); }
        .tab.active { color: var(--text-primary); border-image: linear-gradient(to right, var(--accent-main), var(--accent-contrast)) 1; }

        /* Theme Selector */
        .theme-selector {
            position: absolute;
            top: 20px;
            left: 20px;
            display: flex;
            gap: 10px;
            background: var(--surface-color);
            padding: 8px 15px;
            border-radius: 10px;
            border: 1px solid var(--primary-border-color);
            box-shadow: 0 2px 10px var(--shadow-color);
            transition: all 0.3s ease;
        }
        .theme-option {
            width: 24px;
            height: 24px;
            border-radius: 50%;
            cursor: pointer;
            border: 2px solid transparent;
            transition: all 0.2s ease;
        }
        .theme-option.dark { background-color: #1e1e1e; }
        .theme-option.light { background-color: #ffffff; }
        .theme-option.gray { background-color: #bdbdbd; }
        .theme-option.futuristic { background-color: #00e5ff; }
        .theme-option.retro { background-color: #a8201a; }
        .theme-option.simple { background-color: #3498db; }

        .theme-option.selected {
            border-color: var(--accent-main);
            box-shadow: 0 0 0 3px rgba(var(--text-primary-rgb), 0.3);
        }
        .theme-option:hover {
            transform: scale(1.1);
        }

        .tab-content { display: none; padding: 30px; }
        .tab-content.active { display: block; animation: tab-fade-in 0.5s ease; }
        @keyframes tab-fade-in { from { opacity: 0; } to { opacity: 1; } }

        .controls { display: flex; gap: 15px; margin-bottom: 30px; flex-wrap: wrap; align-items: center; }
        .btn {
            padding: 12px 25px; border: 2px solid transparent; border-radius: 10px; cursor: pointer;
            font-weight: 600; transition: all 0.3s ease; display: flex; align-items: center; gap: 10px;
            font-size: 15px; color: white; text-transform: uppercase; letter-spacing: 0.5px;
        }
        .btn:hover { transform: translateY(-3px) scale(1.05); box-shadow: 0 8px 25px rgba(0,0,0,0.5); }
        .btn-primary { background: linear-gradient(45deg, var(--accent-main), var(--accent-secondary)); border: none; }
        .btn-success { background: linear-gradient(45deg, var(--accent-green), color-mix(in srgb, var(--accent-green) 80%, black 20%)); border: none; }
        .btn-danger { background: linear-gradient(45deg, var(--accent-error), color-mix(in srgb, var(--accent-error) 80%, black 20%)); border: none; }
        .btn-warning { background: linear-gradient(45deg, var(--accent-warning), color-mix(in srgb, var(--accent-warning) 80%, black 20%)); border: none; }
        .btn-secondary { background: var(--text-secondary); border: 2px solid var(--text-secondary); color: var(--text-primary);}


        .search-box { flex: 1; min-width: 250px; position: relative; }
        .search-box input {
            width: 100%; padding: 12px 20px 12px 45px; border: 2px solid var(--primary-border-color);
            background: var(--input-bg); color: var(--input-text); border-radius: 10px; font-size: 16px;
            transition: all 0.3s ease;
        }
        .search-box input:focus { outline: none; border-image: linear-gradient(to right, var(--accent-main), var(--accent-contrast)) 1; }
        .search-box::before { content: '🔍'; position: absolute; left: 15px; top: 50%; transform: translateY(-50%); opacity: 0.6; color: var(--text-secondary); }

        .table-container {
            overflow-x: auto; border: 1px solid var(--primary-border-color);
            border-radius: 15px; max-height: 65vh; overflow-y: auto;
            background: transparent;
        }
        .table-container::-webkit-scrollbar { width: 12px; }
        .table-container::-webkit-scrollbar-track { background: var(--bg-color); }
        .table-container::-webkit-scrollbar-thumb { background-color: var(--secondary-border-color); border-radius: 10px; border: 3px solid var(--bg-color); }
        .table-container::-webkit-scrollbar-thumb:hover { background-color: var(--accent-main); }

        table { width: 100%; border-collapse: collapse; }
        th {
            background: var(--table-header-bg); 
            color: var(--table-header-text); 
            padding: 20px 15px; text-align: center; font-weight: 600;
            position: sticky; top: 0; z-index: 10; 
            border-bottom: var(--table-header-border-bottom);
            font-size: 16px;
        }
        td {
            padding: 15px; 
            border-bottom: var(--table-border-bottom);
            text-align: center; vertical-align: middle; transition: all 0.3s ease;
            color: var(--text-primary);
        }
        tr { transition: background 0.3s ease; }
        tr:nth-child(odd) { background: var(--table-bg-odd); }
        tr:nth-child(even) { background: var(--table-bg-even); }
        tr:not(.highlighted):not(.hidden-row):hover { 
            background: var(--table-row-hover); 
            box-shadow: inset 5px 0 0 var(--accent-warning);
        }

        .editable {
            background: var(--input-bg); 
            border: var(--input-border);
            color: var(--input-text); 
            padding: 10px; border-radius: 8px; width: 100%;
            font-family: inherit; font-size: 15px;
            transition: all 0.3s ease; min-height: 42px; text-align: center; 
        }
        .editable[type="date"]::-webkit-calendar-picker-indicator { filter: invert(var(--theme-invert-filter)); cursor: pointer; }
        .editable:focus {
            outline: none; 
            background: var(--input-bg);
            border-image: linear-gradient(to right, var(--accent-main), var(--accent-secondary)) 1;
        }
        
        .editable.select-field {
            -webkit-appearance: none;
            -moz-appearance: none;
            appearance: none;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='var(--text-secondary)'%3E%3Cpath d='M7 10l5 5 5-5z'/%3E%3C/svg%3E");
            background-repeat: no-repeat;
            background-position: right 10px center;
            background-size: 1em;
            padding-right: 30px;
        }

        tr.highlighted {
            background-color: color-mix(in srgb, var(--highlight-row-color) 20%, transparent);
            box-shadow: inset 7px 0 0 var(--highlight-row-color);
        }
        tr.completed-row {
            opacity: 0.7;
            background-color: color-mix(in srgb, var(--complete-row-color) 15%, transparent);
        }
        tr.completed-row .editable { color: var(--complete-row-color); text-decoration: line-through; }
        tr.hidden-row {
            background-image: repeating-linear-gradient(-45deg, var(--bg-color), var(--bg-color) 10px, rgba(var(--text-primary-rgb), 0.05) 10px, rgba(var(--text-primary-rgb), 0.05) 20px);
            opacity: 0.8;
        }
        tr.hidden-row .editable { color: var(--text-secondary); text-decoration: line-through; opacity: 0.5; }
        
        .particle {
            position: fixed;
            font-size: 24px;
            pointer-events: none;
            z-index: 9999;
            animation: particle-burst 1s ease-out forwards;
        }
        .particle.star { color: var(--accent-warning); text-shadow: 0 0 10px var(--accent-warning); }
        .particle.check { color: var(--accent-green); text-shadow: 0 0 10px var(--accent-green); }
        @keyframes particle-burst {
            0% { transform: translate(0, 0) scale(1); opacity: 1; }
            100% { transform: translate(var(--x), var(--y)) scale(0); opacity: 0; }
        }

        th, td { min-width: 190px; }
        th:nth-child(1), td:nth-child(1) { min-width: 250px; }
        th:nth-child(2), td:nth-child(2) { min-width: 330px; }
        th:nth-child(11), td:nth-child(11) { min-width: 250px; }
        th:nth-child(12), td:nth-child(12) { min-width: 260px; }
        th:nth-child(15), td:nth-child(15) { min-width: 220px; }

        .stats { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 25px; margin-bottom: 30px; }
        .stat-card {
            background: var(--surface-color);
            border: 1px solid var(--primary-border-color); padding: 30px;
            border-radius: 15px; text-align: left; transition: all 0.4s ease;
            position: relative;
            cursor: pointer; 
            overflow: hidden; 
        }
        .stat-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 0 30px rgba(0, 229, 255, 0.3);
            border-color: var(--accent-main);
        }
        .stat-icon {
            font-size: 2.8em; 
            position: absolute;
            top: 20px;
            right: 25px;
            opacity: 0.1;
            transition: all 0.4s ease;
        }
        .stat-card:hover .stat-icon {
            opacity: 0.5;
            transform: scale(1.2) rotate(10deg);
        }
        .stat-number { font-size: 3.8em; font-weight: 700; color: var(--accent-main); }
        .stat-label { font-size: 1.4em; color: var(--text-primary); margin-top: 5px; font-weight: 500;}

        .modal {
            display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.7); backdrop-filter: blur(8px); z-index: 2000;
            align-items: center; justify-content: center;
        }
        .modal.active { display: flex; }
        .modal-content {
            background: var(--surface-color); 
            border-radius: 15px; border: 1px solid var(--secondary-border-color);
            padding: 35px; width: 90%; max-width: 550px; max-height: 85vh;
            overflow-y: auto; animation: modal-appear 0.4s ease-out;
        }
        @keyframes modal-appear { from { opacity: 0; transform: scale(0.9); } to { opacity: 1; transform: scale(1); } }
        
        .form-group { margin-bottom: 15px; }
        .form-group label { display: block; margin-bottom: 8px; font-size: 0.9em; color: var(--text-secondary); }
        .form-group input, .form-group select, .form-group textarea {
            width: 100%; padding: 10px; border: 1px solid var(--primary-border-color);
            background: var(--input-bg); color: var(--input-text); border-radius: 8px;
            font-size: 1em;
            /* For select dropdown arrow */
            -webkit-appearance: none;
            -moz-appearance: none;
            appearance: none;
            background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='var(--text-secondary)'%3E%3Cpath d='M7 10l5 5 5-5z'/%3E%3C/svg%3E");
            background-repeat: no-repeat;
            background-position: right 10px center;
            background-size: 1em;
            padding-right: 30px;
        }
        .form-group textarea { min-height: 80px; resize: vertical; }


        .notification {
            position: fixed; top: 25px; right: 25px; padding: 18px 25px;
            border-radius: 12px; color: #121212; font-weight: 600;
            z-index: 3000; opacity: 0; transform: translateX(120%);
            box-shadow: 0 10px 25px var(--shadow-color);
            transition: all 0.5s cubic-bezier(0.68, -0.55, 0.27, 1.55);
        }
        .notification.success { background: linear-gradient(45deg, var(--accent-green), color-mix(in srgb, var(--accent-green) 80%, black 20%)); }
        .notification.error { background: linear-gradient(45deg, var(--accent-error), color-mix(in srgb, var(--accent-error) 80%, black 20%)); color: white;}
        .notification.info { background: linear-gradient(45deg, var(--accent-main), color-mix(in srgb, var(--accent-main) 80%, black 20%)); }
        .notification.show { opacity: 1; transform: translateX(0); }
        
        .row-actions { display: flex; gap: 8px; justify-content: center; }
        .row-actions button {
            background: var(--surface-color); 
            border: 1px solid var(--primary-border-color); 
            color: var(--text-secondary);
            width: 40px; height: 40px; border-radius: 10px; cursor: pointer;
            transition: all 0.3s ease; font-size: 18px; display: flex; align-items: center; justify-content: center;
        }
        .row-actions button:hover { transform: scale(1.1); }
        .row-actions .highlight-btn:hover { background: var(--accent-warning); color: var(--text-primary); border-color: var(--accent-warning); }
        .row-actions .hide-btn:hover { background: var(--accent-contrast); color: var(--text-primary); border-color: var(--accent-contrast); }
        .row-actions .complete-btn:hover { background: var(--accent-green); color: var(--text-primary); border-color: var(--accent-green); }
        .row-actions .delete-btn:hover { background: var(--accent-error); color: white; border-color: var(--accent-error); }
        .row-actions .transfer-hc-btn:hover { background: var(--accent-main); color: var(--text-primary); border-color: var(--accent-main); }


        .help-section h2 {
            font-size: 2.5em; font-weight: 700; text-align: center; margin-bottom: 40px;
            background: -webkit-linear-gradient(45deg, var(--accent-green), var(--accent-main));
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
        }
        .help-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(350px, 1fr)); gap: 25px; }
        .help-card {
            background: var(--bg-color); border: 1px solid var(--primary-border-color);
            border-radius: 15px; padding: 25px; transition: all 0.3s ease;
        }
        .help-card:hover { border-color: var(--accent-contrast); transform: translateY(-5px); }
        .help-card h3 {
            font-size: 1.5em; color: var(--accent-contrast); margin-bottom: 15px;
            display: flex; align-items: center; gap: 15px;
        }
        .help-card p, .help-card li { color: var(--text-secondary); line-height: 1.7; }
        .help-card ul { list-style: none; padding-left: 0; margin-top: 15px; }
        .help-card li { display: flex; align-items: flex-start; gap: 15px; margin-bottom: 12px; color: var(--text-primary); }
        .help-card ol { margin-top: 10px; padding-left: 20px; color: var(--text-primary); }
        .help-card ol li { margin-bottom: 8px; }
        .help-icon {
            font-size: 24px; min-width: 40px; height: 40px; display: inline-flex;
            align-items: center; justify-content: center; border-radius: 10px;
            background: var(--surface-color); 
            border: 1px solid var(--primary-border-color); 
            margin-top: -5px;
        }

        /* Estagiário Character - Fixed Position */
        .intern-container {
            position: fixed;
            bottom: 20px;
            right: 20px;
            display: flex;
            flex-direction: column;
            align-items: flex-end;
            z-index: 1000;
        }

        .intern-character {
            width: 80px;
            height: 80px;
            background: var(--accent-warning); 
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3em;
            color: var(--character-color);
            box-shadow: 0 5px 15px var(--shadow-color);
            cursor: pointer;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            position: relative;
            margin-bottom: 10px;
            border: 2px solid var(--accent-warning);
        }
        .intern-character::before {
            content: "🧑‍⚖️"; 
            font-size: 1.5em;
        }

        .intern-character:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 8px 20px var(--shadow-color);
        }

        .intern-button {
            background: var(--accent-green); 
            color: white;
            padding: 12px 20px;
            border-radius: 10px;
            border: none;
            cursor: pointer;
            font-weight: 600;
            box-shadow: 0 3px 10px var(--shadow-color);
            transition: background 0.3s ease, transform 0.3s ease, box-shadow 0.3s ease;
        }

        .intern-button:hover {
            background: color-mix(in srgb, var(--accent-green) 80%, black 20%);
            transform: translateY(-2px);
            box-shadow: 0 5px 12px var(--shadow-color);
        }

        .joke-popup {
            position: absolute;
            bottom: calc(100% + 15px);
            right: 0;
            background: var(--surface-color);
            border: 1px solid var(--primary-border-color);
            border-radius: 15px;
            padding: 15px 20px;
            width: 280px;
            box-shadow: 0 5px 20px var(--shadow-color);
            color: var(--text-primary);
            font-size: 0.95em;
            text-align: center;
            opacity: 0;
            visibility: hidden;
            transform: translateY(10px);
            transition: opacity 0.3s ease, transform 0.3s ease, visibility 0.3s ease;
        }

        .joke-popup.active {
            opacity: 1;
            visibility: visible;
            transform: translateY(0);
        }

        .joke-popup::after {
            content: '';
            position: absolute;
            bottom: -10px;
            right: 30px;
            width: 0;
            height: 0;
            border-left: 10px solid transparent;
            border-right: 10px solid transparent;
            border-top: 10px solid var(--surface-color);
        }

        .joke-popup button.close-joke {
            background: none;
            border: none;
            color: var(--text-secondary);
            font-size: 1.2em;
            position: absolute;
            top: 5px;
            right: 5px;
            cursor: pointer;
            transition: color 0.2s ease;
        }
        .joke-popup button.close-joke:hover {
            color: var(--accent-error);
        }

        /* Setor Jurídico Tab Styles */
        .legal-sector-scenario {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            padding: 20px;
            background: var(--surface-color); 
            border-radius: 15px;
            box-shadow: inset 0 0 15px rgba(0,0,0,0.1);
        }

        .legal-character-card {
            background: var(--bg-color); /* Character card background */
            border: 1px solid var(--primary-border-color);
            border-radius: 15px;
            padding: 20px;
            text-align: center;
            box-shadow: 0 5px 15px var(--shadow-color);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: space-between;
            min-height: 300px;
        }

        .character-avatar {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4em;
            margin-bottom: 15px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.2);
            position: relative;
        }

        /* Specific character styles - using theme accents */
        .character-intern .character-avatar { background-color: var(--accent-warning); color: var(--character-color); }
        .character-intern .character-avatar::before { content: "🧑‍⚖️"; font-size: 1em; }
        .character-intern h3 { color: var(--accent-warning); }
        .character-intern button { background: var(--accent-green); }

        .character-specialist .character-avatar { background-color: var(--accent-main); color: var(--character-color); }
        .character-specialist .character-avatar::before { content: "🕵️"; font-size: 1em; }
        .character-specialist h3 { color: var(--accent-main); }
        .character-specialist button { background: var(--accent-main); }

        .character-judge .character-avatar { background-color: var(--accent-error); color: var(--character-color); }
        .character-judge .character-avatar::before { content: "👨‍⚖️"; font-size: 1em; }
        .character-judge h3 { color: var(--accent-error); }
        .character-judge button { background: var(--accent-error); }

        /* New: Advogado da Shopee */
        .character-shopee .character-avatar { background-color: var(--accent-secondary); color: var(--character-color); }
        .character-shopee .character-avatar::before { content: "🤡"; font-size: 1em; }
        .character-shopee h3 { color: var(--accent-secondary); }
        .character-shopee button { background: var(--accent-secondary); }

        /* New: Promotor */
        .character-promotor .character-avatar { background-color: var(--accent-main); color: var(--character-color); }
        .character-promotor .character-avatar::before { content: "🏛️"; font-size: 1em; }
        .character-promotor h3 { color: var(--accent-main); }
        .character-promotor button { background: var(--accent-main); }


        .legal-character-card h3 {
            margin-bottom: 10px;
        }

        .character-response {
            background: var(--input-bg);
            border: 1px solid var(--primary-border-color);
            border-radius: 10px;
            padding: 10px;
            min-height: 60px;
            margin-top: 15px;
            color: var(--input-text);
            text-align: left;
            overflow-y: auto;
            max-height: 100px;
            width: 100%;
        }

        .character-input-area {
            display: flex;
            flex-direction: column;
            gap: 10px;
            width: 100%;
            margin-top: 15px;
        }
        .character-input-area textarea {
            width: 100%;
            padding: 8px;
            border: 1px solid var(--secondary-border-color);
            border-radius: 8px;
            background: var(--input-bg);
            color: var(--input-text);
            resize: vertical;
            min-height: 40px;
            font-family: inherit;
        }
        .character-input-area button {
            width: 100%;
            padding: 10px;
            border-radius: 8px;
            border: none;
            color: white;
            font-weight: 600;
            cursor: pointer;
            transition: background 0.3s ease;
        }
        .intern-pay-section {
            display: flex;
            flex-direction: column;
            gap: 10px;
            width: 100%;
            align-items: center;
        }
        .intern-pay-section input {
            padding: 8px;
            border: 1px solid var(--secondary-border-color);
            border-radius: 8px;
            background: var(--input-bg);
            color: var(--input-text);
            width: 80%;
            text-align: center;
        }
        .intern-pay-section button {
            padding: 10px;
            border-radius: 8px;
            border: none;
            color: white;
            font-weight: 600;
            cursor: not-allowed;
            transition: background 0.3s ease, opacity 0.3s ease;
            opacity: 0.6;
            width: 100%;
        }
        .intern-pay-section button:enabled {
            cursor: pointer;
            opacity: 1;
            background: var(--accent-green);
        }
        .intern-pay-section button:enabled:hover {
            background: color-mix(in srgb, var(--accent-green) 80%, black 20%);
        }
        .intern-pay-message {
            font-size: 0.9em;
            color: var(--text-secondary);
            margin-top: 5px;
        }

    </style>
</head>
<body class="dark-theme"> 
    <audio id="hoverSound" src="https://assets.mixkit.co/sfx/preview/mixkit-sci-fi-click-1123.mp3" preload="auto"></audio>
    <audio id="clickSound" src="https://assets.mixkit.co/sfx/preview/mixkit-system-alert-in-membrane-200.mp3" preload="auto"></audio>
    <audio id="tabClickSound" src="https://assets.mixkit.co/sfx/preview/mixkit-game-bling-2070.mp3" preload="auto"></audio>
    <audio id="policeSirenSound" src="https://assets.mixkit.co/sfx/preview/mixkit-police-siren-1647.mp3" preload="auto"></audio>

    <div class="container">
        <div class="header">
            <h1>Controle de Réus Presos</h1>
            <p>Gestão e Acompanhamento Processual</p>
            <div id="saveStatus" class="save-status">Salvo Localmente</div>
            
            <div class="theme-selector">
                <div class="theme-option dark" title="Tema Escuro" onclick="setTheme('dark')"></div>
                <div class="theme-option light" title="Tema Claro" onclick="setTheme('light')"></div>
                <div class="theme-option gray" title="Tema Cinza" onclick="setTheme('gray')"></div>
                <div class="theme-option futuristic" title="Tema Futurista" onclick="setTheme('futuristic')"></div>
                <div class="theme-option retro" title="Tema Retrô" onclick="setTheme('retro')"></div>
                <div class="theme-option simple" title="Tema Simples" onclick="setTheme('simple')"></div>
            </div>
        </div>

        <div class="tabs">
            <button class="tab active" onclick="showTab('instrucao', this)">📋 Processos em Instrução</button>
            <button class="tab" onclick="showTab('juri', this)">👨‍⚖️ Processos para Júri</button>
            <button class="tab" onclick="showTab('hc', this)">⚖️ Processos Aptos para HC</button>
            <button class="tab" onclick="showTab('setorJuridico', this)">🏛️ Setor Jurídico</button> <button class="tab" onclick="showTab('ajuda', this)">❓ Ajuda</button>
        </div>

        <div id="instrucao" class="tab-content active">
            <div class="stats">
                <div class="stat-card" onclick="filterTableByCrime('instrucao', '')"><span class="stat-icon">📄</span><div class="stat-number" id="totalInstrucao">64</div><div class="stat-label">Total de Processos</div></div>
                <div class="stat-card" onclick="filterTableByCrime('instrucao', 'Tráfico')"><span class="stat-icon">⚖️</span><div class="stat-number" id="trafico">35</div><div class="stat-label">Tráfico</div></div>
                <div class="stat-card" onclick="filterTableByCrime('instrucao', 'Furto')"><span class="stat-icon">💰</span><div class="stat-number" id="furto">12</div><div class="stat-label">Furto</div></div>
                <div class="stat-card" onclick="filterTableByCrime('instrucao', 'Roubo')"><span class="stat-icon">🔪</span><div class="stat-number" id="roubo">6</div><div class="stat-label">Roubo</div></div>
            </div>
            <div class="controls">
                <button class="btn btn-primary" onclick="openModal('instrucao')">➕ Adicionar</button>
                <button class="btn btn-primary" onclick="sortByName('instrucao')">A-Z Ordenar</button>
                <button class="btn btn-success" onclick="document.getElementById('importInstrucao').click()">📤 Importar</button>
                <input type="file" id="importInstrucao" style="display: none;" accept=".csv" onchange="importData(event, 'instrucao')">
                <button class="btn btn-success" onclick="exportData('instrucao')">📊 Exportar</button>
                <button class="btn btn-warning" onclick="saveAllData()">💾 Salvar</button>
                <button class="btn btn-secondary" id="showHiddenInstrucaoBtn" style="display:none;" onclick="showAllHidden('instrucao')">👁️ Mostrar Ocultos</button>
                <button class="btn btn-danger" onclick="clearData('instrucao')">🗑️ Limpar Tudo</button>
                <div class="search-box">
                    <input type="text" id="searchInstrucao" placeholder="Buscar em processos de instrução..." onkeyup="searchTable('instrucao')">
                </div>
            </div>
            <div class="table-container">
                <table id="tableInstrucao">
                    <thead>
                        <tr>
                            <th>Autos</th><th>Nome do Réu</th><th>Data Prisão</th><th>Crime</th><th>Remessa IP</th><th>Data da Denúncia</th><th>Recebimento Denúncia</th><th>Data da Audiência</th><th>Data Sentença</th><th>Defesa</th><th>Fase do Processo</th><th>Observação</th><th>Tempo Preso</th><th>Atendimento na Floramar</th><th>Ações</th><th>Link Externo</th>
                        </tr>
                    </thead>
                    <tbody id="tbodyInstrucao"></tbody>
                </table>
            </div>
        </div>

        <div id="juri" class="tab-content">
             <div class="stats">
                <div class="stat-card" onclick="filterTableByJuriStatus('juri', '')"><span class="stat-icon">📄</span><div class="stat-number" id="totalJuri">8</div><div class="stat-label">Total de Processos</div></div>
                <div class="stat-card" onclick="filterTableByJuriStatus('juri', 'pronunciado')"><span class="stat-icon">👨‍⚖️</span><div class="stat-number" id="pronunciados">6</div><div class="stat-label">Pronunciados</div></div>
                <div class="stat-card" onclick="filterTableByJuriStatus('juri', 'agendado')"><span class="stat-icon">🗓️</span><div class="stat-number" id="agendados">4</div><div class="stat-label">Sessões Agendadas</div></div>
                <div class="stat-card" onclick="filterTableByJuriStatus('juri', 'suspenso')"><span class="stat-icon">🛑</span><div class="stat-number" id="suspensos">2</div><div class="stat-label">Suspensos (Art. 366)</div></div>
            </div>
            <div class="controls">
                <button class="btn btn-primary" onclick="openModal('juri')">➕ Adicionar</button>
                <button class="btn btn-primary" onclick="sortByName('juri')">A-Z Ordenar</button>
                <button class="btn btn-success" onclick="document.getElementById('importJuri').click()">📤 Importar</button>
                <input type="file" id="importJuri" style="display: none;" accept=".csv" onchange="importData(event, 'juri')">
                <button class="btn btn-success" onclick="exportData('juri')">📊 Exportar</button>
                <button class="btn btn-warning" onclick="saveAllData()">💾 Salvar</button>
                <button class="btn btn-secondary" id="showHiddenJuriBtn" style="display:none;" onclick="showAllHidden('juri')">👁️ Mostrar Ocultos</button>
                <button class="btn btn-danger" onclick="clearData('juri')">🗑️ Limpar Tudo</button>
                <div class="search-box">
                    <input type="text" id="searchJuri" placeholder="Buscar em processos de júri..." onkeyup="searchTable('juri')">
                </div>
            </div>
            <div class="table-container">
                <table id="tableJuri">
                    <thead>
                        <tr>
                            <th>Autos</th><th>Réu</th><th>Data do Fato</th><th>AIJ</th><th>Pronúncia</th><th>Trânsito</th><th>Data Sessão</th><th>Observações</th><th>Ações</th>
                        </tr>
                    </thead>
                    <tbody id="tbodyJuri"></tbody>
                </table>
            </div>
        </div>

        <div id="hc" class="tab-content">
            <div class="stats">
                <div class="stat-card" onclick="filterTableByHcAptitude('')"><span class="stat-icon">📄</span><div class="stat-number" id="totalHc">0</div><div class="stat-label">Total de Processos HC</div></div>
                <div class="stat-card" onclick="filterTableByHcAptitude('apto')"><span class="stat-icon">✅</span><div class="stat-number" id="hcAptos">0</div><div class="stat-label">Aptos para HC</div></div>
                </div>
            <div class="controls">
                <button class="btn btn-primary" onclick="openModal('hc')">➕ Adicionar HC</button>
                <button class="btn btn-primary" onclick="sortByName('hc')">A-Z Ordenar</button>
                <button class="btn btn-success" onclick="document.getElementById('importHc').click()">📤 Importar</button>
                <input type="file" id="importHc" style="display: none;" accept=".csv" onchange="importData(event, 'hc')">
                <button class="btn btn-success" onclick="exportData('hc')">📊 Exportar</button>
                <button class="btn btn-warning" onclick="saveAllData()">💾 Salvar</button>
                <button class="btn btn-secondary" id="showHiddenHcBtn" style="display:none;" onclick="showAllHidden('hc')">👁️ Mostrar Ocultos</button>
                <button class="btn btn-danger" onclick="clearData('hc')">🗑️ Limpar Tudo</button>
                <div class="search-box">
                    <input type="text" id="searchHc" placeholder="Buscar em processos HC..." onkeyup="searchTable('hc')">
                </div>
            </div>
            <div class="table-container">
                <table id="tableHc">
                    <thead>
                        <tr>
                            <th>Autos</th><th>Nome do Réu</th><th>Motivo Aptidão HC</th><th>Observação HC</th><th>Ações</th>
                        </tr>
                    </thead>
                    <tbody id="tbodyHc"></tbody>
                </table>
            </div>
        </div>

        <div id="setorJuridico" class="tab-content">
            <div class="legal-sector-scenario">
                <div class="legal-character-card character-intern">
                    <div class="character-avatar"></div>
                    <h3>Estagiário</h3>
                    <p>Sempre pronto para uma piada jurídica!</p>
                    <div class="character-response" id="internResponse"></div>
                    <button class="btn btn-primary" onclick="showInternJoke()">Fale com o Estagiário</button>
                    <div class="intern-pay-section">
                        <label for="internPayment">Pagamento ao Estagiário:</label>
                        <input type="number" id="internPayment" min="0" value="0" oninput="checkPayment('intern')">
                        <button id="internSecretButton" class="btn btn-primary" disabled onclick="triggerSecretResource('intern')">Acesso Secreto do Estagiário</button>
                        <span id="internPayMessage" class="intern-pay-message">Pague mais de R$ 1.000 para liberar!</span>
                    </div>
                </div>

                <div class="legal-character-card character-specialist">
                    <div class="character-avatar"></div>
                    <h3>Especialista no Crime</h3>
                    <p>Conselhos estratégicos (e um pouco sarcásticos).</p>
                    <div class="character-response" id="specialistResponse"></div>
                    <div class="character-input-area">
                        <textarea id="specialistInput" placeholder="Peça um conselho..."></textarea>
                        <button class="btn btn-success" onclick="getSpecialistAdvice()">Pedir Conselho</button>
                    </div>
                    <div class="intern-pay-section">
                        <label for="specialistPayment">Pagamento ao Especialista:</label>
                        <input type="number" id="specialistPayment" min="0" value="0" oninput="checkPayment('specialist')">
                        <button id="specialistSecretButton" class="btn btn-success" disabled onclick="triggerSecretResource('specialist')">Acesso Secreto do Especialista</button>
                        <span id="specialistPayMessage" class="intern-pay-message">Pague mais de R$ 10.000 para liberar!</span>
                    </div>
                </div>

                <div class="legal-character-card character-shopee">
                    <div class="character-avatar"></div>
                    <h3>Advogado da Shopee</h3>
                    <p>Conselhos jurídicos com preço de banana!</p>
                    <div class="character-response" id="shopeeResponse"></div>
                    <div class="character-input-area">
                        <textarea id="shopeeInput" placeholder="Qual a sua dúvida jurídica?"></textarea>
                        <button class="btn btn-secondary" onclick="getShopeeAdvice()">Perguntar ao Shopee</button>
                    </div>
                    <div class="intern-pay-section">
                        <label for="shopeePayment">Pagamento ao Adv. Shopee:</label>
                        <input type="number" id="shopeePayment" min="0" value="0" oninput="checkPayment('shopee')">
                        <button id="shopeeSecretButton" class="btn btn-secondary" disabled onclick="triggerSecretResource('shopee')">Acesso Secreto do Shopee</button>
                        <span id="shopeePayMessage" class="intern-pay-message">Pague mais de R$ 200 para liberar!</span>
                    </div>
                </div>
                <div class="legal-character-card character-judge">
                    <div class="character-avatar"></div>
                    <h3>O Juiz</h3>
                    <p>Sua petição? Indeferida! (Provavelmente).</p>
                    <div class="character-response" id="judgeResponse"></div>
                    <div class="character-input-area">
                        <textarea id="judgeInput" placeholder="Faça seu pedido..."></textarea>
                        <button class="btn btn-danger" onclick="getJudgeVerdict()">Apresentar Petição</button>
                    </div>
                    <div class="intern-pay-section">
                        <label for="judgePayment">Pagamento ao Juiz:</label>
                        <input type="number" id="judgePayment" min="0" value="0" oninput="checkPayment('judge')">
                        <button id="judgeSecretButton" class="btn btn-danger" disabled onclick="triggerSecretResource('judge')">Acesso Secreto do Juiz</button>
                        <span id="judgePayMessage" class="intern-pay-message">Pague mais de R$ 50.000 para liberar!</span>
                    </div>
                </div>

                <div class="legal-character-card character-promotor">
                    <div class="character-avatar"></div>
                    <h3>O Promotor</h3>
                    <p>A lei acima de tudo. Sem atalhos!</p>
                    <div class="character-response" id="promotorResponse"></div>
                    <div class="character-input-area">
                        <textarea id="promotorInput" placeholder="Apresente seus argumentos..."></textarea>
                        <button class="btn btn-primary" onclick="getPromotorResponse()">Fale com o Promotor</button>
                    </div>
                     <div class="intern-pay-section">
                        <label for="promotorPayment">Pagamento ao Promotor:</label>
                        <input type="number" id="promotorPayment" min="0" value="0" oninput="checkPayment('promotor')">
                        <button id="promotorSecretButton" class="btn btn-primary" disabled onclick="triggerSecretResource('promotor')">Acesso Secreto do Promotor</button>
                        <span id="promotorPayMessage" class="intern-pay-message">Pague mais de R$ 100.000 para liberar!</span>
                    </div>
                </div>
                </div>
        </div>
        
        <div id="ajuda" class="tab-content">
            <div class="help-section">
                <h2>Guia de Recursos</h2>
                <div class="help-grid">
                     <div class="help-card">
                        <h3><span class="help-icon">💡</span> Como Importar do Excel</h3>
                        <p>Esta aplicação não lê arquivos `.xlsx` diretamente. Para importar seus dados, você deve primeiro salvá-los no formato correto:</p>
                        <ol>
                            <li>Abra sua planilha no Excel ou Google Sheets.</li>
                            <li>Vá em <strong>Arquivo > Salvar Como</strong> (ou Fazer o Download).</li>
                            <li>Na opção "Tipo de arquivo", selecione <strong>"CSV UTF-8 (Delimitado por vírgulas) (*.csv)"</strong>. Este é o formato mais compatível.</li>
                            <li>Salve o novo arquivo `.csv` em seu computador.</li>
                            <li>Use o botão <strong>📤 Importar</strong> na aplicação para carregar este arquivo.</li>
                        </ol>
                    </div>
                    <div class="help-card">
                        <h3><span class="help-icon">⚙️</span> Controles Principais</h3>
                        <ul>
                            <li><span class="help-icon">➕</span> Adiciona um novo processo à tabela atual.</li>
                            <li><span class="help-icon">A-Z</span> Organiza a tabela em ordem alfabética pelo nome do réu.</li>
                             <li><span class="help-icon">📤</span> Importa dados de um arquivo .CSV para atualizar ou adicionar processos em massa.</li>
                            <li><span class="help-icon">📊</span> Exporta os dados da tabela visível para um arquivo CSV (compatível com Excel).</li>
                            <li><span class="help-icon">💾</span> Salva todas as suas alterações no armazenamento local do navegador.</li>
                            <li><span class="help-icon">👁️</span> Aparece quando há linhas ocultas e permite reexibi-las.</li>
                        </ul>
                    </div>
                    <div class="help-card">
                        <h3><span class="help-icon">🚀</span> Ações por Linha</h3>
                        <p>Cada processo possui botões de ação rápida para gerenciamento:</p>
                        <ul>
                            <li><span class="help-icon" style="color: var(--accent-warning);">⭐</span><strong>Evidenciar:</strong> Destaca a linha com uma cor dourada para casos prioritários.</li>
                            <li><span class="help-icon" style="color: var(--accent-green);">✅</span><strong>Concluir:</strong> Marca a linha como finalizada, com estilo verde e texto riscado.</li>
                            <li><span class="help-icon" style="color: var(--accent-contrast);">👁️</span><strong>Ocultar:</strong> Aplica uma faixa escura na linha para desativá-la visualmente sem apagar.</li>
                            <li><span class="help-icon" style="color: var(--accent-error);">🗑️</span><strong>Deletar:</strong> Exclui permanentemente a linha da tabela (pede confirmação).</li>
                            <li><span class="help-icon" style="color: var(--accent-main);">➡️</span><strong>Mover para HC:</strong> Mover o processo para a aba "Processos Aptos para HC".</li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>

    </div>

    <div id="modal" class="modal">
        <div class="modal-content">
            <h2 id="modalTitle">Adicionar Processo</h2>
            <form id="processForm">
                <div id="formFields"></div>
                <div style="display: flex; gap: 10px; margin-top: 20px;">
                    <button type="submit" class="btn btn-success">Salvar</button>
                    <button type="button" class="btn btn-danger" onclick="closeModal()">Cancelar</button>
                </div>
            </form>
        </div>
    </div>

    <div id="notification" class="notification">Dados salvos com sucesso!</div>

    <script>
        let dataInstrucao = [];
        let dataJuri = [];
        let dataHc = [];
        let currentTable = '';
        let unsavedChanges = false;
        const saveStatusEl = document.getElementById('saveStatus');
        let currentInstrucaoFilter = '';
        let currentJuriFilter = '';
        let currentHcFilter = '';

        // Audio elements
        const hoverSound = document.getElementById('hoverSound');
        const clickSound = document.getElementById('clickSound');
        const tabClickSound = document.getElementById('tabClickSound');
        const policeSirenSound = document.getElementById('policeSirenSound');


        // Frases Prontas do Estagiário
        const internJokes = [
            "Doutor, eu juro que imprimi as petições... só não sei onde as coloquei.",
            "Posso ir buscar um café? É para fins de... jurisprudência cafeeira.",
            "Pelo que eu entendi do 'Código Penal para Leigos', estamos ferrados.",
            "Meu maior sonho é ter um carimbo. Um dia chegarei lá!",
            "Minha vida se resume a café e cópias.",
            "Ser estagiário de direito é ter a OAB da paciência.",
            "O dia que eu não tirar cópia, acho que me demitem.",
            "Meu maior sonho é não ouvir 'faz um cafezinho?'",
            "Resumo do dia: mais tinta pra impressora.",
            "Jurava que ia julgar, mas só assino lista.",
            "Sua petição é urgente, mas minha dignidade é mais.",
            "Sobrevivendo um prazo de cada vez.",
            "Ainda procurando o 'direito' no estágio.",
            "Meu plano de carreira: um dia, ter meu próprio carimbo.",
            "Será que se eu imprimir colorida a petição, ela tem mais chance de ser deferida?",
            "Meu maior medo não é perder um prazo, é perder a caneta.",
            "Eu devia ganhar por passo que dou no fórum, não por hora.",
            "Minha aula mais importante na faculdade foi a de como sobreviver com café.",
            "Um dia, eu vou ter um estagiário e vou mandar ele tirar cópia de um livro inteiro. Brincadeira... ou não?",
            "Meu sonho de consumo é um dia ver meu nome em uma intimação, e não o 'por estagiário'.",
            "Se eu já aprendi alguma coisa, é que 'urgente' no meio jurídico significa 'pra ontem e era pra ontem, mas agora é pra daqui a pouco'.",
            "Às vezes, eu me pergunto se meu chefe lembra meu nome ou só me chama de 'ei, estagiário!'"
        ];

        // Recurso Desbloqueado do Estagiário (agora funcionalidade interna)
        const internUnlockedResources = [
            "Estagiário: 'Recomendo a leitura do Art. 187 do Código do Trava-Língua Jurídico: 'Todo réu será declarado inocente se o advogado conseguir pronunciar 3x 'inconstitucionalissimamente' sem gaguejar!' (O estagiário tropeça, derruba papéis, mas sorri vitorioso) *Dica: Tente falar isso rápido 3 vezes!*",
            "Estagiário: 'Descobri uma nova jurisprudência! O caso do 'Habeas Corpus do Delivery Atrasado', onde a pena foi convertida em 50 pizzas gratuitas. Inovador!' (Ele aponta para um documento que parece ser uma conta de pizzaria.) *Recurso: Pizza Grátis Habilitada! (Visualmente)*",
            "Estagiário: 'Minha pesquisa aponta que a melhor defesa é a distração. Que tal um show de mágica na próxima audiência? A lei não proíbe a ilusionismo processual!' (Ele tenta fazer uma moeda desaparecer, sem sucesso.) *Efeito Visual: Moeda Sumindo!*",
            "Estagiário: 'Baseado no princípio da 'economia processual do cafezinho', sugiro que a sentença seja ditada durante o coffee break, para otimizar o tempo e a cafeína! (Ele pega um copo de café e o cheira intensamente.) *Funcionalidade: Modo 'Coffee Break' Ativado! (Altera a cor do texto para marrom por 3s)*"
        ];


        // Frases Prontas do Especialista no Crime
        const specialistPhrases = [
            "Na minha experiência, a melhor defesa é uma boa fuga. Mas, para vocês, temos que seguir o 'protocolo'.",
            "Não é um crime se ninguém for pego, certo? Brincadeira... ou não?",
            "Essa galera do direito vive no mundo da lua. Aqui fora, a lei é outra.",
            "Onde está o suborno? Ah, desculpe, quis dizer... a 'colaboração estratégica'?"
        ];
        // Recurso Desbloqueado do Especialista (agora funcionalidade interna)
        const specialistUnlockedResources = [
            "Especialista: 'Dica Subversiva: Se o réu alegar amnésia seletiva por trauma de infância causado por jingles de shopping, pode colar. É a jurisprudência da 'síndrome do Black Friday'.' (Ele retira um chapéu de aba larga do paletó e pisca.) *Visual: Chapéu de Aba Larga Adicionado ao Avatar!*",
            "Especialista: 'Dica Subversiva: Crie uma cortina de fumaça jurídica. Sugira uma teoria da conspiração envolvendo pombos-correio e o sumiço de uma caneta. A corte adora um bom mistério!' (Ele aponta para um canto escuro da sala, com um sorriso enigmático.) *Efeito: Fumaça Misteriosa Aparece!*",
            "Especialista: 'Dica Subversiva: Meu conselho é: encontre um bode expiatório com um nome parecido. A confusão pode gerar um 'erro judiciário simpático'. Acredite, funciona mais do que parece.' (Ele coça o queixo pensativo, como se estivesse avaliando a vida.) *Funcionalidade: Sugerir um nome de bode expiatório aleatório. (Mostra um nome fictício)*",
            "Especialista: 'Dica Subversiva: Já tentou a defesa do 'sonambulismo contábil'? O réu comete crimes enquanto dorme e organiza as finanças. É infalível... ou talvez não.' (Ele pega um bloco de notas e anota algo rapidamente, com uma expressão séria.) *Visual: Bloco de Notas Contábil Aparece!*"
        ];


        // Advogado da Shopee Functions
        const shopeePhrases = [
            "Se o réu comprar três crimes, o quarto sai com frete grátis?",
            "Doutor, podemos emitir um cupom de desconto para a pena?",
            "Minha argumentação tem 99% de chance de ser bem avaliada pelos clientes... quero dizer, pelo júri.",
            "Precisamos otimizar a rota da justiça para evitar taxas de importação inesperadas!"
        ];
        // Recurso Desbloqueado do Advogado da Shopee (agora funcionalidade interna)
        const shopeeUnlockedResources = [
            "Advogado da Shopee: 'Oferta relâmpago! Proponho que a pena seja convertida em mil 'shopee moedas' e uma avaliação 5 estrelas para o sistema prisional. Imperdível!' (Ele puxa um smartphone e tenta escanear o ar em busca de cupons invisíveis.) *Funcionalidade: Botão 'Comprar Pena' Ativado! (Adiciona um botão falso)*",
            "Advogado da Shopee: 'Exclusivo! Acabei de encontrar um 'bug' na lei que permite trocar a prisão por 100 horas de 'curtidas' em fotos de gatos na internet. É a 'jurisprudência do engajamento social'! Vai viralizar!' (He digita freneticamente no smartphone.) *Efeito: Curtidas e Corações Flutuam!*",
            "Advogado da Shopee: 'Black Friday do Direito! Sugiro que o réu cumpra a pena em 'cashback'. A cada dia livre, ele recebe 1% de volta da fiança paga. É a justiça com ROI!' (He gesticula como um vendedor de televisão.) *Visual: Dinheiro Voando!*",
            "Advogado da Shopee: 'Urgentíssimo! Descobri um cupom 'FREELAW' que isenta o réu de todas as acusações se ele assinar a newsletter do nosso escritório. É o 'marketing jurídico 4.0' em ação!' (He estende um panfleto imaginário com um QR Code.) *Funcionalidade: Gerar QR Code para 'Desconto Jurídico'! (Mostra um QR Code genérico)*"
        ];


        // Frases Prontas do Juiz
        const judgePhrases = [
            "Ordem na corte! Ou terei que aplicar a 'lei do silêncio' com um martelo.",
            "Alguém me traga mais café. A justiça é lenta, e minha paciência também.",
            "Eu declaro... que essa discussão está me dando dor de cabeça.",
            "Próximo! Meu tempo é tão valioso quanto uma sentença bem fundamentada... ou um feriado prolongado."
        ];
        // Recurso Desbloqueado do Juiz (agora funcionalidade interna)
        const judgeUnlockedResources = [
            "Juiz: (bate o martelo freneticamente) 'Declaro este caso... um mistério insolúvel como as instruções de montagem de um móvel sueco! Todos em recesso por tempo indeterminado!' (A área de respostas de todos os outros personagens é limpa, simulando confusão geral.) *Efeito: Limpa respostas dos outros personagens!*",
            "Juiz: (bate o martelo suavemente) 'Após profunda deliberação, decido que... o réu deve recitar o alfabeto ao contrário! Isso é um teste de memória, e da minha paciência!' (A área de respostas de todos os outros personagens é limpa, simulando confusão generalizada.) *Funcionalidade: Ativa 'Modo Alfabeto ao Contrário'! (Adiciona texto desafiador)*",
            "Juiz: (bate o martelo com força) 'Causa suspensa! A partir de agora, todas as partes devem se comunicar apenas por mímica até que eu decida o contrário!' (A área de respostas de todos os outros personagens é limpa, simulando confusão generalizada.) *Efeito: Esconde campos de input de texto dos outros personagens!*",
            "Juiz: (bate o martelo no ritmo de uma música) 'A sentença é... depende do clima! Se estiver sol, inocente! Se chover, culpado! A meteorologia tem sido uma aliada interessante na minha corte!' (A área de respostas de todos os outros personagens é limpa, simulando confusão generalizada.) *Funcionalidade: Exibe o clima atual e uma 'sentença' baseada nele!*"
        ];


        // Frases Prontas do Promotor
        const promotorPhrases = [
            "A verdade, Excelência, é como um cupom de 50% de desconto: indiscutível!",
            "Prevejo a condenação do réu com a mesma clareza que vejo meu próximo bônus.",
            "Meus argumentos são tão sólidos quanto a conexão de internet da Shopee em dia de pico.",
            "A justiça não dorme, mas às vezes eu tiro uma soneca estratégica para pensar em mais acusações."
        ];
        // Recurso Desbloqueado do Promotor (Ele não aceita dinheiro, mas tem um comportamento único)
        const promotorUnlockedResources = [
            "Promotor: 'Discurso Vazio, Efeito Máximo: Cidadãos, a lei é a balança inabalável da sociedade! Minha paixão pela justiça é tão pura quanto uma planilha bem organizada. Não há valor material que corrompa o dever de um Promotor! Sua tentativa é um ultraje à toga!' (Ele pega um monóculo e o limpa dramaticamente, olhando para o vazio.) *Visual: Monóculo Aparece no Avatar!*",
            "Promotor: 'Discurso Vazio, Efeito Máximo: A defesa pode tentar subverter a ordem, mas o Ministério Público, em sua retidão inquestionável, permanecerá firme como um algoritmo bem programado. Desisto de ouvir essas propostas pecuniárias ultrajantes!' (Ele gesticula grandiosamente com as mãos, como se estivesse discursando para uma multidão invisível.) *Efeito: Um gráfico de 'Integridade' aparece e sobe!*",
            "Promotor: 'Discurso Vazio, Efeito Máximo: A honra e a integridade da promotoria não estão à venda! Meus argumentos são forjados na legalidade e na moralidade, não no vil metal. Seu 'pagamento' é uma afronta ao sistema!' (Ele cruza os braços e ergue o nariz, com um ar de superioridade moral.) *Funcionalidade: Bloqueia a possibilidade de pagar os outros personagens por 5 segundos!*"
        ];

        // Sample Data (kept as is)
        const exemploInstrucao = [
            ["5013375-82.2025.8.13.0223", "Adriano Antonio Rodrigues", "2025-05-19", "Tráfico", "2025-06-25", "2025-06-26", "2025-07-18", "2025-10-02", "", "Defensoria Pública", "", "", "", false, false, false],
            ["5015162-49.2025.8.13.0223", "Adriano Pinto", "2025-07-16", "Roubo Impróprio", "", "", "", "", "", "", "", "", "", false, false, false],
            ["5008762-19.2025.8.13.0223", "Alysson Fernandes Lima", "2025-04-24", "Furto", "2025-04-29", "2025-04-30", "2025-05-05", "2025-08-20", "", "Defensoria Pública", "", "", "", false, false, false],
            ["0022457-62.2024.8.13.0223", "Breno Henrique Almeida Gonçalves", "2024-12-06", "Roubo", "2024-12-12", "2024-12-17", "2024-12-19", "", "", "Defensoria Pública", "", "Suspenso-em 16/01/2025", "", false, false, false],
            ["5011235-75.2025.8.13.0223", "Breno Rodrigo Moreira e Sueli", "2025-05-26", "Tráfico", "2025-05-29", "2025-06-06", "2025-06-27", "2025-11-12", "", "Defensoria Pública", "", "", "", false, false, false],
            ["5006501-81.2025.8.13.0223", "Breno Rodrigues e Larissa", "2025-04-29", "Tráfico", "2024-07-10", "2024-08-06", "2025-05-16", "2025-10-01", "", "Defensoria Pública", "", "", "", false, false, false],
            ["", "Cláudio Gonçalves Eugênio", "2025-07-15", "Lesão", "", "", "", "", "", "", "", "", "", false, false, false],
            ["5009341-64.2025.8.13.0223", "Derick Henrique Alves do Nascimento", "2025-05-03", "Tráfico", "2025-05-08", "2025-05-12", "2025-06-13", "2025-10-22", "", "Defensoria Pública", "", "", "", false, false, false],
            ["5012621-43.2025.8.13.0223", "Eriberto de Oliveira", "2025-04-27", "Tráfico", "2025-06-13", "2025-06-26", "2025-07-18", "2025-08-07", "", "", "", "", "", false, false, false],
            ["5009615-28.2025.8.13.0223", "Ezequiel Erezi Silva", "2025-05-03", "Roubo", "2025-05-12", "2025-05-13", "2025-05-13", "2025-08-27", "", "", "", "", "", false, false, false],
            ["5010099-43.2025.8.13.0223", "Gabriel Henrique Silva", "2025-05-08", "Tráfico", "2025-05-16", "2025-05-20", "2025-06-13", "2025-10-22", "", "Defensoria Pública", "", "", "", false, false, false],
            ["5008187-11.2025.8.13.0223", "Hilton Eduardo Cardoso da Fonseca", "2025-04-12", "Trânsito", "2025-04-22", "2025-04-25", "2025-04-28", "2025-07-30", "", "Defensoria Pública", "", "", "", false, false, false],
            ["5013083-97.2025.8.13.0223", "Igor Gruen de Paula", "2025-06-12", "Furto", "2025-06-26", "2025-06-25", "2025-06-26", "2025-09-03", "", "", "", "", "", false, false, false],
            ["0003579-55.2025.8.13.0223", "Isabel Cristina Pacheco de Oliveira", "2025-01-28", "Tráfico", "2025-02-27", "2025-03-12", "2025-04-02", "2024-06-25", "", "Defensoria Pública", "", "", "", false, false, false],
            ["0005152-31.2025.8.13.0223", "Israel Junio dos Santos", "2025-02-26", "Tráfico", "2025-03-25", "", "2025-05-20", "2025-08-06", "", "Defensoria Pública", "", "", "", false, false, false],
            ["", "João Paulo Alves de Moura", "2025-07-08", "Homicídio", "", "", "", "", "", "", "", "", "", false, false, false],
            ["5008495-47.2025.8.13.0223", "Jonathan Flainer da Silva", "2025-04-16", "Furto", "2025-04-25", "2025-04-29", "2025-04-30", "2025-07-30", "", "Defensoria Pública", "", "", "", false, false, false],
            ["0014600-28.2025.8.13.0223", "Julio Cezar Borges Rocha", "2025-04-14", "Roubo", "2025-04-15", "2025-05-20", "2025-05-21", "2025-07-03", "", "Defensoria Pública", "", "", "", false, false, false],
            ["", "Marcos e Leonardo", "2025-07-15", "Roubo", "", "", "", "", "","Defensoria Pública", "", "", "", false, false, false],
            ["5009492-30.2025.8.13.0223", "Rafael Aparecido Carlos", "2025-05-03", "Furto", "2025-05-09", "2025-05-30", "2025-06-05", "2025-08-06", "", "Defensoria Pública", "", "", "", false, false, false],
            ["0019024-50.2024.8.13.0223", "Rafael Rodrigues de Oliveira", "2024-09-22", "Homicidio", "2024-10-01", "2024-10-09", "2024-10-11", "2025-07-25", "", "Defensoria Pública", "", "", "", false, false, false],
            ["5009346-86.2025.8.13.0223", "Rafael Santos Natividade e Bruna Estefane Silva", "2025-07-02", "Furto Qualificado", "2025-05-08", "2025-05-14", "2025-05-23", "", "", "Defensoria Pública", "", "", "", false, false, false],
            ["0005301-27.2025.8.13.0223", "Rayner Geraldo Delfino", "2025-02-27", "Tráfico", "2025-03-26", "2025-04-01", "2025-05-13", "2025-08-06", "", "Defensoria Pública", "", "", "", false, false, false],
            ["5008511-98.2025.8.13.0223", "Reynaldo Teixeira dos Santos", "2025-04-17", "Furto", "2025-04-25", "2025-04-28", "2025-04-28", "2025-08-06", "", "Defensoria Pública", "", "", "", false, false, false],
            ["0013941-19.2025.8.13.0223", "Thaliz Gomes Dinis", "2025-04-06", "Tráfico", "2025-04-14", "2025-04-29", "2025-05-21", "2025-09-10", "", "Defensoria Pública e Constituida", "", "", "", false, false, false],
            ["0007083-69.2025.8.13.0223", "Thiago Benfenatti Corgosinho", "2025-03-13", "Tráfico", "2025-04-04", "2025-03-14", "2025-05-20", "2025-08-27", "", "Defensoria Pública", "", "", "", false, false, false],
            ["", "Tiago Ferreira Vilela", "2025-07-17", "Lesão", "", "", "", "", "", "", "", "", "", false, false, false],
            ["5008846-20.2025.8.13.0223", "Waldir Silva Domingos", "2025-04-28", "Tráfico", "2025-04-30", "2025-05-06", "2025-06-13", "2025-10-22", "", "Defensoria Pública", "", "", "", false, false, false],
            ["0004221-28.2025.8.13.0223", "Watylla, Marco Tulio e Ronaldo", "2025-03-05", "Furto", "2025-03-13", "2025-03-21", "2025-03-29", "2025-06-24", "", "Defensoria Pública", "", "", "", false, false, false],
            ["5008590-77.2025.8.13.0223", "Weliton José Pereira", "2025-04-20", "Tráfico", "2025-04-28", "2025-04-30", "", "2025-10-01", "", "Defensoria Pública", "", "", "", false, false, false],
            ["0003686-02.2025.8.13.0223", "Ycaro e Fabrício", "2025-02-13", "Tráfico", "2025-03-07", "2025-03-14", "2025-04-25", "2025-07-30", "", "Defensoria Pública e Constituida", "", "", "", false, false, false]
        ];

        const exemploJuri = [
            ["0009124-43.2024.8.13.0223", "Genival da Silva", "2024-06-09", "2024-09-16", "2024-10-18", "2025-05-29", "2025-09-30", "", false, false, false],
            ["0010718-92.2024.8.13.0223", "Nathan Paulo Cezarino", "2024-06-30", "SUSPENSO", "", "", "", "SUSPENSO", false, false, false],
            ["0019024-50.2024.8.13.0223", "Rafael Rodrigues de Oliveira", "", "2025-06-26", "", "", "", "", false, false, false],
            ["5007058-05.2024.8.13.0223", "Weslley dos Santos Silva", "2024-09-04", "2025-01-14", "2025-03-22", "2025-04-22", "2025-08-13", "", false, false, false]
        ];

        const exemploHc = [
            ["5013375-82.2025.8.13.0223", "Adriano Antonio Rodriques", "Excesso de Prazo", "Processo parado há 180 dias sem movimentação.", false, false, false],
            ["0004349-82.2024.8.13.0223", "Fábio e Gustavo", "Prisão Ilegal", "Não há fundamentação para a manutenção da prisão.", false, false, false]
        ];
        
        const colunasInstrucao = ['autos', 'nomeReu', 'dataPrisao', 'crime', 'remessaIP', 'dataDenuncia', 'recebimentoDenuncia', 'dataAudiencia', 'dataSentenca', 'defesa', 'faseProcesso', 'observacao', 'atendimentoFloramar'];
        const colunasJuri = ['autos', 'reu', 'dataFato', 'aij', 'pronuncia', 'transito', 'dataSessao', 'observacoes'];
        const colunasHc = ['autos', 'nomeReu', 'motivoAptidaoHc', 'observacaoHc'];
        
        function showTab(tabName, element) {
            document.querySelectorAll('.tab-content').forEach(c => c.classList.remove('active'));
            document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
            document.getElementById(tabName).classList.add('active');
            element.classList.add('active');
            currentInstrucaoFilter = ''; 
            currentJuriFilter = '';
            currentHcFilter = '';
            // Only render tables that are currently active
            if (tabName !== 'setorJuridico' && tabName !== 'ajuda') {
                renderTable(tabName);
            }
            // Close any open joke popups when changing tabs
            closeJokePopup();
            playTabClickSound(); // Play sound on tab click
        }

        function formatDateForInput(dateStr) {
            if (!dateStr || dateStr.includes('-')) return dateStr; 
            const parts = dateStr.split('/');
            if (parts.length !== 3) return dateStr; 
            let [day, month, year] = parts;
            if (year.length === 2) {
                year = `20${year}`;
            }
            return `${year}-${month.padStart(2, '0')}-${day.padStart(2, '0')}`;
        }
        
        function calculateDaysSince(dateString) {
            if (!dateString) return 'N/A';
            const arrestDate = new Date(dateString);
            arrestDate.setMinutes(arrestDate.getMinutes() + arrestDate.getTimezoneOffset());
            
            const today = new Date();
            today.setHours(0, 0, 0, 0);
            
            const diffTime = today.getTime() - arrestDate.getTime();
            const diffDays = Math.floor(diffTime / (1000 * 3600 * 24));
            return diffDays >= 0 ? `${diffDays} dias` : 'Data futura';
        }

        function loadFromStorage() {
            const savedInstrucao = localStorage.getItem('dataInstrucao');
            const savedJuri = localStorage.getItem('dataJuri');
            const savedHc = localStorage.getItem('dataHc');

            let instrucaoTemp = savedInstrucao ? JSON.parse(savedInstrucao) : exemploInstrucao.map(r => [...r]);
            let juriTemp = savedJuri ? JSON.parse(savedJuri) : exemploJuri.map(r => [...r]);
            let hcTemp = savedHc ? JSON.parse(savedHc) : exemploHc.map(r => [...r]);

            const dateColumnsInstrucao = [2, 4, 5, 6, 7, 8];
            const dateColumnsJuri = [2, 3, 4, 5, 6];

            instrucaoTemp.forEach(row => dateColumnsInstrucao.forEach(i => row[i] = formatDateForInput(row[i])));
            juriTemp.forEach(row => dateColumnsJuri.forEach(i => row[i] = formatDateForInput(row[i])));
            
            dataInstrucao = instrucaoTemp;
            dataJuri = juriTemp;
            dataHc = hcTemp;
            
            const instrucaoCols = colunasInstrucao.length + 3;
            dataInstrucao.forEach(row => { while (row.length < instrucaoCols) row.push(false); });
            const juriCols = colunasJuri.length + 3;
            dataJuri.forEach(row => { while (row.length < juriCols) row.push(false); });
            const hcCols = colunasHc.length + 3;
            dataHc.forEach(row => { while (row.length < hcCols) row.push(false); });

            renderAllTables();
            updateAllStats();
            updateSaveStatus(false);

            const savedTheme = localStorage.getItem('selectedTheme');
            setTheme(savedTheme || 'dark');
        }
        
        function saveAllData() {
            try {
                localStorage.setItem('dataInstrucao', JSON.stringify(dataInstrucao));
                localStorage.setItem('dataJuri', JSON.stringify(dataJuri));
                localStorage.setItem('dataHc', JSON.stringify(dataHc));
                updateSaveStatus(false);
                showNotification('Dados salvos com sucesso!', 'success');
                playClickSound(); // Play sound on save
            } catch (e) {
                showNotification('Erro ao salvar os dados.', 'error');
                console.error("Save error:", e);
            }
        }
        
        function markUnsavedChanges() {
            if (!unsavedChanges) {
                 updateSaveStatus(true);
            }
            unsavedChanges = true;
        }

        function updateSaveStatus(hasUnsavedChanges) {
            if (hasUnsavedChanges) {
                saveStatusEl.textContent = 'Alterações não salvas';
                saveStatusEl.style.background = 'var(--accent-warning)';
                saveStatusEl.style.color = '#121212';
            } else {
                saveStatusEl.textContent = 'Salvo Localmente';
                saveStatusEl.style.background = 'var(--accent-green)';
                saveStatusEl.style.color = '#121212';
            }
        }

        function renderAllTables() {
            renderTable('instrucao');
            renderTable('juri');
            renderTable('hc');
            checkHiddenRows();
        }

        function renderTable(type) {
            const tbody = document.getElementById(`tbody${type.charAt(0).toUpperCase() + type.slice(1)}`);
            const data = type === 'instrucao' ? dataInstrucao : (type === 'juri' ? dataJuri : dataHc);
            const columns = type === 'instrucao' ? colunasInstrucao : (type === 'juri' ? colunasJuri : colunasHc);
            tbody.innerHTML = '';

            data.forEach((row, index) => {
                let displayRow = true;
                if (type === 'instrucao' && currentInstrucaoFilter !== '') {
                    const crimeValue = (row[3] || '').toUpperCase();
                    if (!crimeValue.includes(currentInstrucaoFilter.toUpperCase())) {
                        displayRow = false;
                    }
                } else if (type === 'juri' && currentJuriFilter !== '') {
                    if (currentJuriFilter === 'pronunciado') {
                        if (!row[4] || row[4] === '') displayRow = false;
                    } else if (currentJuriFilter === 'agendado') {
                        if (!row[6] || row[6] === '') displayRow = false;
                    } else if (currentJuriFilter === 'suspenso') {
                        if (!(row[7] || '').toLowerCase().includes('suspenso')) displayRow = false;
                    }
                } else if (type === 'hc' && currentHcFilter === 'apto') {
                    if (!row[2] || row[2] === '' || row[2] === 'Não Apto') {
                        displayRow = false;
                    }
                }

                if (!displayRow) return;

                const tr = document.createElement('tr');
                tr.id = `row-${type}-${index}`;
                
                const isHighlighted = row[columns.length];
                const isCompleted = row[columns.length + 1];
                const isHidden = row[columns.length + 2];
                if (isHighlighted) tr.classList.add('highlighted');
                if (isCompleted) tr.classList.add('completed-row');
                if (isHidden) tr.classList.add('hidden-row');

                // Add mouseover/mouseout listeners for navigation sound
                tr.addEventListener('mouseover', () => playHoverSound());
                // No mouseout needed as hover sound is quick

                columns.forEach((col, cellIndex) => {
                    const td = document.createElement('td');
                    td.appendChild(createInputElement(getInputType(type, cellIndex), row[cellIndex], type, index, cellIndex));
                    tr.appendChild(td);
                });

                const actionTd = document.createElement('td');
                let actionButtonsHtml = `
                    <button class="highlight-btn" onclick="toggleFlag(event, '${type}', ${index}, 'highlight')" title="Evidenciar">⭐</button>
                    <button class="complete-btn" onclick="toggleFlag(event, '${type}', ${index}, 'complete')" title="Concluir">✅</button>
                    <button class="hide-btn" onclick="toggleFlag(event, '${type}', ${index}, 'hide')" title="Ocultar">👁️</button>
                    <button class="delete-btn" onclick="deleteRow('${type}', ${index})" title="Excluir">🗑️</button>`;

                if (type === 'instrucao') {
                    actionButtonsHtml += `<button class="transfer-hc-btn" onclick="transferToHc(event, ${index})" title="Mover para HC">➡️</button>`;

                    const tempoPresoTd = document.createElement('td');
                    tempoPresoTd.textContent = calculateDaysSince(row[2]);
                    tr.insertBefore(tempoPresoTd, tr.children[12]);
                    tr.insertBefore(actionTd, tr.children[14]);
                    const linkTd = document.createElement('td');
                    linkTd.innerHTML = `<button class="btn btn-primary" style="padding: 8px 12px; font-size: 14px;" onclick="window.open('https://drive.google.com/drive/folders/11sPHIaYBkcVLlRA_2uxWrjhibNDL72GD?usp=sharing', '_blank')">🔗 Link</button>`;
                    linkTd.querySelector('button').addEventListener('click', () => playClickSound());
                    tr.appendChild(linkTd);
                } else {
                    tr.appendChild(actionTd);
                }
                
                actionTd.innerHTML = `<div class="row-actions">${actionButtonsHtml}</div>`;
                actionTd.querySelectorAll('button').forEach(button => {
                    button.addEventListener('click', () => playClickSound());
                });


                tbody.appendChild(tr);
            });
        }
        
        function getInputType(type, cellIndex) {
            const dateColumnsInstrucao = [2, 4, 5, 6, 7, 8];
            const dateColumnsJuri = [2, 3, 4, 5, 6];
            const selectColumns = {
                'instrucao': { 9: ['Defensoria Pública', 'Advogado Particular'], 12: ['Atendido', 'Não Atendido', 'Recusou Atendimento'] },
                'juri': {},
                'hc': { 2: ['Excesso de Prazo', 'Ausência de Justa Causa', 'Prisão Ilegal', 'Outros', 'Não Apto'] }
            };
            
            if (type === 'instrucao' && dateColumnsInstrucao.includes(cellIndex)) return 'date';
            if (type === 'juri' && dateColumnsJuri.includes(cellIndex)) return 'date';

            if (selectColumns[type]?.[cellIndex]) {
                if (selectColumns[type][cellIndex].length > 0) {
                    return { type: 'select', options: selectColumns[type][cellIndex] };
                } else {
                    return 'text';
                }
            }
            return 'text';
        }

        function createInputElement(inputType, value, type, rowIndex, cellIndex) {
            let element;
            if (typeof inputType === 'object' && inputType.type === 'select') {
                element = document.createElement('select');
                element.className = 'editable select-field';
                element.innerHTML = `<option value="">Selecione...</option>` + 
                    inputType.options.map(option => `<option value="${option}" ${option === value ? 'selected' : ''}>${option}</option>`).join('');
            } else {
                element = document.createElement('input');
                element.type = inputType;
                element.className = 'editable';
                element.value = value || '';
            }
            element.addEventListener('change', function() { 
                updateCell(type, rowIndex, cellIndex, this.value);
                playClickSound(); // Play sound on cell edit
            });
            return element;
        }

        function updateCell(type, rowIndex, cellIndex, value) {
            const data = type === 'instrucao' ? dataInstrucao : (type === 'juri' ? dataJuri : dataHc);
            data[rowIndex][cellIndex] = value;
            if (type === 'instrucao' && cellIndex === 2) { renderTable('instrucao'); }
            updateStats(type);
            markUnsavedChanges();
        }

        function toggleFlag(event, type, index, flagType) {
            const data = type === 'instrucao' ? dataInstrucao : (type === 'juri' ? dataJuri : dataHc);
            const columns = type === 'instrucao' ? colunasInstrucao : (type === 'juri' ? colunasJuri : colunasHc);
            const columnsLength = columns.length;
            let flagIndex;
            let particleChar = '';
            let particleClass = '';

            if (flagType === 'highlight') {
                flagIndex = columnsLength;
                particleChar = '⭐';
                particleClass = 'star';
            } else if (flagType === 'complete') {
                flagIndex = columnsLength + 1;
                particleChar = '✅';
                particleClass = 'check';
            } else if (flagType === 'hide') {
                flagIndex = columnsLength + 2;
            }
            
            data[index][flagIndex] = !data[index][flagIndex];
            markUnsavedChanges();
            
            const tr = document.getElementById(`row-${type}-${index}`);
            
            if (flagType === 'highlight' || flagType === 'complete') {
                tr.classList.toggle(flagType === 'highlight' ? 'highlighted' : 'completed-row');
                if (data[index][flagIndex]) {
                    createParticleEffect(event.target, particleChar, particleClass);
                }
            } else {
                tr.classList.toggle('hidden-row');
            }

            checkHiddenRows();
        }
        
        function createParticleEffect(buttonElement, particleChar, cssClass) {
            const rect = buttonElement.getBoundingClientRect();
            const originX = rect.left + rect.width / 2;
            const originY = rect.top + rect.height / 2;

            for (let i = 0; i < 10; i++) {
                const p = document.createElement('span');
                p.innerHTML = particleChar;
                p.classList.add('particle', cssClass);
                
                const angle = Math.random() * 2 * Math.PI;
                const radius = Math.random() * 100 + 50;
                const x = Math.cos(angle) * radius;
                const y = Math.sin(angle) * radius;

                p.style.left = `${originX}px`;
                p.style.top = `${originY}px`;
                p.style.setProperty('--x', `${x}px`);
                p.style.setProperty('--y', `${y}px`);
                
                document.body.appendChild(p);
                setTimeout(() => {
                    p.remove();
                }, 1000);
            }
        }

        function checkHiddenRows() {
            const hasHiddenInstrucao = dataInstrucao.some(row => row[colunasInstrucao.length + 2]);
            const hasHiddenJuri = dataJuri.some(row => row[colunasJuri.length + 2]);
            const hasHiddenHc = dataHc.some(row => row[colunasHc.length + 2]);

            document.getElementById('showHiddenInstrucaoBtn').style.display = hasHiddenInstrucao ? 'flex' : 'none';
            document.getElementById('showHiddenJuriBtn').style.display = hasHiddenJuri ? 'flex' : 'none';
            document.getElementById('showHiddenHcBtn').style.display = hasHiddenHc ? 'flex' : 'none';
        }

        function showAllHidden(type) {
            const data = type === 'instrucao' ? dataInstrucao : (type === 'juri' ? dataJuri : dataHc);
            const columns = type === 'instrucao' ? colunasInstrucao : (type === 'juri' ? colunasJuri : colunasHc);
            const hideFlagIndex = columns.length + 2;
            data.forEach(row => { row[hideFlagIndex] = false; });
            markUnsavedChanges();
            renderTable(type);
            playClickSound(); // Play sound on showing hidden rows
        }

        function deleteRow(type, index) {
            if (confirm('Tem certeza que deseja EXCLUIR este processo permanentemente?')) {
                const data = type === 'instrucao' ? dataInstrucao : (type === 'juri' ? dataJuri : dataHc);
                data.splice(index, 1);
                markUnsavedChanges();
                renderTable(type);
                updateStats(type);
                showNotification('Processo excluído.', 'info');
                playClickSound(); // Play sound on delete
            }
        }

        function sortByName(type) {
            const data = type === 'instrucao' ? dataInstrucao : (type === 'juri' ? dataJuri : dataHc);
            data.sort((a, b) => {
                const nameA = a[1] || '';
                const nameB = b[1] || '';
                return nameA.localeCompare(nameB, 'pt-BR', { sensitivity: 'base' });
            });
            markUnsavedChanges();
            renderTable(type);
            showNotification('Tabela ordenada por nome.', 'info');
            playClickSound(); // Play sound on sort
        }

        function openModal(type) {
            currentTable = type;
            const modalTitle = document.getElementById('modalTitle');
            const formFields = document.getElementById('formFields');
            modalTitle.textContent = `Adicionar Processo ${type === 'instrucao' ? 'em Instrução' : (type === 'juri' ? 'para Júri' : 'para HC')}`;
            
            if (type === 'instrucao') {
                formFields.innerHTML = `
                    <div class="form-group"><label>Número dos Autos</label><input type="text" name="autos"></div>
                    <div class="form-group"><label>Nome do Réu</label><input type="text" name="nomeReu"></div>
                    <div class="form-group"><label>Data da Prisão</label><input type="date" name="dataPrisao"></div>
                    <div class="form-group"><label>Crime</label><input type="text" name="crime"></div>
                    <div class="form-group"><label>Remessa IP</label><input type="date" name="remessaIP"></div>
                    <div class="form-group"><label>Data da Denúncia</label><input type="date" name="dataDenuncia"></div>
                    <div class="form-group"><label>Recebimento Denúncia</label><input type="date" name="recebimentoDenuncia"></div>
                    <div class="form-group"><label>Data da Audiência</label><input type="date" name="dataAudiencia"></div>
                    <div class="form-group"><label>Data Sentença</label><input type="date" name="dataSentenca"></div>
                    <div class="form-group"><label>Defesa</label><select name="defesa"><option value="">Selecione...</option><option>Defensoria Pública</option><option>Advogado Particular</option></select></div>
                    <div class="form-group"><label>Fase do Processo</label><input type="text" name="faseProcesso"></div>
                    <div class="form-group"><label>Observação</label><textarea name="observacao"></textarea></div>
                    <div class="form-group"><label>Atendimento na Floramar</label><select name="atendimentoFloramar"><option value="">Selecione...</option><option>Atendido</option><option>Não Atendido</option><option>Recusou Atendimento</option></select></div>`;
            } else if (type === 'juri') {
                formFields.innerHTML = `
                    <div class="form-group"><label>Número dos Autos</label><input type="text" name="autos"></div>
                    <div class="form-group"><label>Réu</label><input type="text" name="reu"></div>
                    <div class="form-group"><label>Data do Fato</label><input type="date" name="dataFato"></div>
                    <div class="form-group"><label>AIJ</label><input type="date" name="aij"></div>
                    <div class="form-group"><label>Pronúncia</label><input type="date" name="pronuncia"></div>
                    <div class="form-group"><label>Trânsito</label><input type="date" name="transito"></div>
                    <div class="form-group"><label>Data Sessão</label><input type="date" name="dataSessao"></div>
                    <div class="form-group"><label>Observações</label><textarea name="observacoes"></textarea></div>`;
            } else if (type === 'hc') {
                formFields.innerHTML = `
                    <div class="form-group"><label>Número dos Autos</label><input type="text" name="autos"></div>
                    <div class="form-group"><label>Nome do Réu</label><input type="text" name="nomeReu"></div>
                    <div class="form-group"><label>Motivo da Aptidão HC</label>
                        <select name="motivoAptidaoHc">
                            <option value="">Selecione...</option>
                            <option value="Excesso de Prazo">Excesso de Prazo</option>
                            <option value="Ausência de Justa Causa">Ausência de Justa Causa</option>
                            <option value="Prisão Ilegal">Prisão Ilegal</option>
                            <option value="Outros">Outros</option>
                            <option value="Não Apto">Não Apto</option>
                        </select>
                    </div>
                    <div class="form-group"><label>Observação HC</label><textarea name="observacaoHc"></textarea></div>`;
            }
            document.getElementById('processForm').reset();
            document.getElementById('modal').classList.add('active');
            playClickSound(); // Play sound on opening modal
        }

        function closeModal() {
            document.getElementById('modal').classList.remove('active');
            playClickSound(); // Play sound on closing modal
        }
        
        document.getElementById('processForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const formData = new FormData(this);
            const colunas = currentTable === 'instrucao' ? colunasInstrucao : (currentTable === 'juri' ? colunasJuri : colunasHc);
            const newRow = colunas.map(col => formData.get(col) || '');
            newRow.push(false, false, false);
            if (currentTable === 'instrucao') {
                dataInstrucao.push(newRow);
            } else if (currentTable === 'juri') {
                dataJuri.push(newRow);
            } else if (currentTable === 'hc') {
                dataHc.push(newRow);
            }
            renderTable(currentTable); updateStats(currentTable); markUnsavedChanges();
            closeModal();
            showNotification('Processo adicionado!', 'success');
            playClickSound(); // Play sound on adding process
        });
        
        function clearData(type) {
            if (confirm(`Tem certeza que deseja limpar TODOS os dados da tabela de ${type}?`)) {
                if (type === 'instrucao') dataInstrucao = [];
                else if (type === 'juri') dataJuri = [];
                else if (type === 'hc') dataHc = [];
                renderTable(type); updateStats(type); markUnsavedChanges();
                showNotification('Tabela limpa.', 'info');
                playClickSound(); // Play sound on clearing data
            }
        }

        function updateAllStats() {
            updateStats('instrucao');
            updateStats('juri');
            updateStats('hc');
        }
        
        function updateStats(type) {
            const data = type === 'instrucao' ? dataInstrucao : (type === 'juri' ? dataJuri : dataHc);
            if (type === 'instrucao') {
                document.getElementById('totalInstrucao').textContent = data.length;
                document.getElementById('trafico').textContent = data.filter(r => (r[3] || '').toUpperCase().includes('TRÁFICO')).length;
                document.getElementById('furto').textContent = data.filter(r => (r[3] || '').toUpperCase().includes('FURTO')).length;
                document.getElementById('roubo').textContent = data.filter(r => (r[3] || '').toUpperCase().includes('ROUBO')).length;
            } else if (type === 'juri') {
                document.getElementById('totalJuri').textContent = data.length;
                document.getElementById('pronunciados').textContent = data.filter(r => r[4] && r[4] !== '').length;
                document.getElementById('agendados').textContent = data.filter(r => r[6] && r[6] !== '').length;
                document.getElementById('suspensos').textContent = data.filter(r => (r[7] || '').toLowerCase().includes('suspenso')).length;
            } else if (type === 'hc') {
                document.getElementById('totalHc').textContent = data.length;
                document.getElementById('hcAptos').textContent = data.filter(r => r[2] && r[2] !== '' && r[2] !== 'Não Apto').length;
            }
        }
        
        function searchTable(type) {
            const filter = document.getElementById(`search${type.charAt(0).toUpperCase() + type.slice(1)}`).value.toUpperCase();
            const rows = document.getElementById(`tbody${type.charAt(0).toUpperCase() + type.slice(1)}`).getElementsByTagName("tr");
            const data = type === 'instrucao' ? dataInstrucao : (type === 'juri' ? dataJuri : dataHc);

            for (let i = 0; i < rows.length; i++) {
                const row = rows[i];
                let rowData = data[i];

                let rowText = '';
                for (let j = 0; j < (type === 'instrucao' ? colunasInstrucao.length : (type === 'juri' ? colunasJuri.length : colunasHc.length)); j++) {
                    rowText += (rowData[j] || '') + ' ';
                }

                const matchesSearch = rowText.toUpperCase().indexOf(filter) > -1;

                let matchesTableFilter = true;
                if (type === 'instrucao') {
                    if (currentInstrucaoFilter !== '') {
                        const crimeValue = (rowData[3] || '').toUpperCase();
                        matchesTableFilter = crimeValue.includes(currentInstrucaoFilter.toUpperCase());
                    }
                } else if (type === 'juri') {
                    if (currentJuriFilter === 'pronunciado') {
                        matchesTableFilter = (rowData[4] && rowData[4] !== '');
                    } else if (currentJuriFilter === 'agendado') {
                        matchesTableFilter = (rowData[6] && rowData[6] !== '');
                    } else if (currentJuriFilter === 'suspenso') {
                        matchesTableFilter = (rowData[7] || '').toLowerCase().includes('suspenso');
                    } else if (currentJuriFilter === '') {
                        matchesTableFilter = true;
                    }
                } else if (type === 'hc') {
                    if (currentHcFilter === 'apto') {
                        matchesTableFilter = (rowData[2] && rowData[2] !== '' && rowData[2] !== 'Não Apto');
                    } else if (currentHcFilter === '') {
                        matchesTableFilter = true;
                    }
                }

                if (matchesSearch && matchesTableFilter) {
                    row.style.display = "";
                } else {
                    row.style.display = "none";
                }
            }
        }

        function filterTableByCrime(type, crimeType) {
            currentInstrucaoFilter = crimeType;
            renderTable(type);
            playClickSound(); // Play sound on filter
        }

        function filterTableByJuriStatus(type, statusType) {
            currentJuriFilter = statusType;
            renderTable(type);
            playClickSound(); // Play sound on filter
        }

        function filterTableByHcAptitude(aptitudeType) {
            currentHcFilter = aptitudeType;
            renderTable('hc');
            playClickSound(); // Play sound on filter
        }
        
        function importData(event, type) {
            const file = event.target.files[0];
            if (!file) { return; }
            
            const reader = new FileReader();
            reader.onload = function(e) {
                const text = e.target.result;
                const data = type === 'instrucao' ? dataInstrucao : (type === 'juri' ? dataJuri : dataHc);
                const columns = type === 'instrucao' ? colunasInstrucao : (type === 'juri' ? colunasJuri : colunasHc);

                const headerSynonyms = {
                    'autos': ['autos', 'número dos autos'], 'nomeReu': ['nome do réu', 'réu'], 'dataPrisao': ['data prisão', 'data da prisão'], 'crime': ['crime'],
                    'remessaIP': ['remessa ip', 'remessa do ip'], 'dataDenuncia': ['data da denúncia', 'data denúncia'],
                    'recebimentoDenuncia': ['recebimento denúncia', 'recebimento da denúncia', 'recebimento data'],
                    'dataAudiencia': ['data da audiência', 'data audiência'], 'dataSentenca': ['data sentença', 'data da sentença'],
                    'defesa': ['defesa'], 'faseProcesso': ['fase do processo'], 'observacao': ['observação', 'observações'],
                    'atendimentoFloramar': ['atendimento na floramar', 'floramar'], 'dataFato': ['data do fato'], 'aij': ['aij'],
                    'pronuncia': ['pronúncia'], 'transito': ['trânsito'], 'dataSessao': ['data sessão', 'data da sessão'],
                    'motivoAptidaoHc': ['motivo aptidão hc', 'motivo hc', 'aptidão hc'], 'observacaoHc': ['observação hc', 'obs hc']
                };

                function findKeyBySynonym(headerName) {
                    const cleanedHeader = headerName.toLowerCase().trim().replace(/"/g, '');
                    for(const key in headerSynonyms) {
                        if (headerSynonyms[key].includes(cleanedHeader)) return key;
                    }
                    return null;
                }

                try {
                    const rows = text.split(/\r\n|\n/);
                    if (rows.length < 2) {
                        showNotification('Arquivo CSV inválido ou vazio.', 'error');
                        return;
                    }

                    const firstLine = rows[0];
                    const commaCount = (firstLine.match(/,/g) || []).length;
                    const semicolonCount = (firstLine.match(/;/g) || []).length;
                    const delimiter = semicolonCount > commaCount ? ';' : ',';
                    
                    const csvHeaders = firstLine.split(delimiter);
                    const columnIndexMap = {};
                    const internalColumnMap = {};

                    columns.forEach((key, index) => {
                        internalColumnMap[key.toLowerCase()] = index;
                    });
                    
                    csvHeaders.forEach((header, index) => {
                        const key = findKeyBySynonym(header);
                        if (key && internalColumnMap[key.toLowerCase()] !== undefined) {
                            columnIndexMap[internalColumnMap[key.toLowerCase()]] = index;
                        }
                    });

                    if (Object.keys(columnIndexMap).length === 0) {
                        showNotification('Cabeçalho não reconhecido. Verifique se os nomes das colunas no arquivo correspondem aos da tabela.', 'error');
                        return;
                    }
                    
                    const existingDataMap = new Map();
                    data.forEach(row => {
                        const autosIndex = internalColumnMap['autos'];
                        if (autosIndex !== undefined) {
                            existingDataMap.set(row[autosIndex], row);
                        }
                    });

                    rows.slice(1).forEach(rowStr => {
                        if (!rowStr.trim()) return;
                        const importedRow = rowStr.split(delimiter).map(cell => cell.trim().replace(/"/g, ''));
                        
                        const autosIndexInInternalCols = internalColumnMap['autos'];
                        const importedCaseNumberIndexInCsv = columnIndexMap[autosIndexInInternalCols];
                        
                        if (importedCaseNumberIndexInCsv === undefined || !importedRow[importedCaseNumberIndexInCsv]) {
                            return; 
                        }
                        const caseNumber = importedRow[importedCaseNumberIndexInCsv];

                        if (existingDataMap.has(caseNumber)) {
                            const existingRow = existingDataMap.get(caseNumber);
                            columns.forEach((colKey, colIndex) => {
                                const importIndex = columnIndexMap[colIndex];
                                if (importIndex !== undefined && importedRow[importIndex] !== undefined) {
                                    let value = importedRow[importIndex];
                                    if(getInputType(type, colIndex) === 'date') {
                                        value = formatDateForInput(value);
                                    }
                                    existingRow[colIndex] = value;
                                }
                            });
                        } else {
                            const newRow = new Array(columns.length).fill('');
                            columns.forEach((colKey, colIndex) => {
                                const importIndex = columnIndexMap[colIndex];
                                if (importIndex !== undefined && importedRow[importIndex] !== undefined) {
                                     let value = importedRow[importIndex];
                                     if(getInputType(type, colIndex) === 'date') {
                                        value = formatDateForInput(value);
                                    }
                                    newRow[colIndex] = value;
                                }
                            });
                            newRow.push(false, false, false);
                            data.push(newRow);
                        }
                    });

                    markUnsavedChanges();
                    renderAllTables();
                    updateAllStats();
                    showNotification('Dados importados com sucesso!', 'success');
                    playClickSound(); // Play sound on import
                } catch (error) {
                    showNotification('Erro ao importar o arquivo. Verifique o formato ou o cabeçalho do CSV.', 'error');
                    console.error("Erro na importação:", error);
                }
            };
            reader.onerror = () => {
                showNotification('Não foi possível ler o arquivo.', 'error');
            };
            reader.readAsText(file, 'UTF-8');
            event.target.value = null;
        }

        function exportData(type) {
            const data = type === 'instrucao' ? dataInstrucao : (type === 'juri' ? dataJuri : dataHc);
             if (data.length === 0) {
                showNotification('Não há dados para exportar.', 'error'); return;
            }
            let headers, dataToExport;
            if (type === 'instrucao') {
                headers = ['Autos', 'Nome do Réu', 'Data Prisão', 'Crime', 'Remessa IP', 'Data da Denúncia', 'Recebimento Denúncia', 'Data da Audiência', 'Data Sentença', 'Defesa', 'Fase do Processo', 'Observação', 'Tempo Preso', 'Atendimento na Floramar'];
                dataToExport = data.map(row => {
                    const dataPortion = row.slice(0, colunasInstrucao.length);
                    const tempoPreso = calculateDaysSince(dataPortion[2]);
                    const finalRow = [...dataPortion];
                    finalRow.splice(12, 0, tempoPreso);
                    return finalRow.slice(0, headers.length);
                });
            } else if (type === 'juri') {
                headers = ['Autos', 'Réu', 'Data do Fato', 'AIJ', 'Pronúncia', 'Trânsito', 'Data Sessão', 'Observações'];
                dataToExport = data.map(row => row.slice(0, colunasJuri.length));
            } else if (type === 'hc') {
                headers = ['Autos', 'Nome do Réu', 'Motivo Aptidão HC', 'Observação HC'];
                dataToExport = data.map(row => row.slice(0, colunasHc.length));
            }
            let csvContent = "data:text/csv;charset=utf-8," + headers.join(";") + "\n" 
                + dataToExport.map(r => r.map(c => `"${(c || '').replace(/"/g, '""')}"`).join(";")).join("\n");
            const link = document.createElement("a");
            link.setAttribute("href", encodeURI(csvContent));
            link.setAttribute("download", `export_${type}_${new Date().toISOString().slice(0,10)}.csv`);
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
            playClickSound(); // Play sound on export
        }

        function showNotification(message, type = 'info') {
            const notification = document.getElementById('notification');
            notification.textContent = message;
            notification.className = `notification show ${type}`;
            setTimeout(() => { notification.className = 'notification'; }, 3000);
        }

        function transferToHc(event, index) {
            if (confirm('Deseja mover este processo para a aba "Processos Aptos para HC"?')) {
                const processToTransfer = dataInstrucao[index];

                const newHcEntry = [
                    processToTransfer[0],
                    processToTransfer[1],
                    '',
                    ''
                ];

                newHcEntry.push(false, false, false);

                dataHc.push(newHcEntry);

                dataInstrucao.splice(index, 1);

                markUnsavedChanges();
                renderAllTables();
                updateAllStats();
                showNotification('Processo movido para a aba HC!', 'success');
                playClickSound(); // Play sound on transfer
            }
        }

        // Estagiário Joke Functions
        function showInternJoke() {
            const internResponseDiv = document.getElementById('internResponse');
            const randomIndex = Math.floor(Math.random() * internJokes.length);
            internResponseDiv.textContent = internJokes[randomIndex];
            setTimeout(() => internResponseDiv.textContent = '', 5000);
            playClickSound(); // Play sound on intern joke
        }
        // Intern Unlockable Resource (updated for internal functionality)
        function getInternUnlockedResource() {
            const internResponseDiv = document.getElementById('internResponse');
            const randomIndex = Math.floor(Math.random() * internUnlockedResources.length);
            const resourceText = internUnlockedResources[randomIndex];
            internResponseDiv.textContent = resourceText;

            // Specific visual/functional effects for Intern
            if (resourceText.includes('Pizza Grátis')) {
                const avatar = document.querySelector('.character-intern .character-avatar');
                const pizzaEmoji = document.createElement('span');
                pizzaEmoji.textContent = '🍕';
                pizzaEmoji.style.fontSize = '2em';
                pizzaEmoji.style.position = 'absolute';
                pizzaEmoji.style.top = '10px';
                pizzaEmoji.style.right = '10px';
                avatar.appendChild(pizzaEmoji);
                setTimeout(() => pizzaEmoji.remove(), 3000);
            } else if (resourceText.includes('Moeda Sumindo')) {
                const internCard = document.querySelector('.character-intern');
                const coin = document.createElement('span');
                coin.textContent = '🪙';
                coin.style.fontSize = '2em';
                coin.style.position = 'absolute';
                coin.style.top = '50%';
                coin.style.left = '50%';
                coin.style.transform = 'translate(-50%, -50%)';
                coin.style.transition = 'all 1s ease-out';
                internCard.appendChild(coin);
                setTimeout(() => {
                    coin.style.opacity = '0';
                    coin.style.transform = 'translate(-50%, -150%) scale(0.1)';
                }, 100);
                setTimeout(() => coin.remove(), 1100);
            } else if (resourceText.includes('Modo \'Coffee Break\' Ativado!')) {
                internResponseDiv.style.color = 'brown';
                setTimeout(() => internResponseDiv.style.color = 'var(--input-text)', 3000);
            }
            playClickSound();
        }


        // Specialist Advice Functions (Simulated NLP)
        function getSpecialistAdvice() {
            const specialistInput = document.getElementById('specialistInput');
            const specialistResponseDiv = document.getElementById('specialistResponse');
            const query = specialistInput.value.toLowerCase();
            let response = '';

            if (query.includes('crime') || query.includes('furtar') || query.includes('roubo') || query.includes('matar') || query.includes('pena')) {
                response = specialistPhrases[0]; // "Na minha experiência, a melhor defesa é uma boa fuga..."
            } else if (query.includes('prazo') || query.includes('tempo')) {
                response = "Prazos? São apenas sugestões com consequências graves. A dica de ouro é: se não deu tempo de fazer bem, faça parecer que deu. A proatividade é a irmã da procrastinação, só que mais bem vestida.";
            } else if (query.includes('prova') || query.includes('evidencia')) {
                response = "Provas? Às vezes, a melhor prova é a que não existe. Ou a que sumiu misteriosamente. Brincadeira! (Ou não?) A verdade é maleável, dependendo de quem a apresenta e com que sotaque.";
            } else if (query.includes('cliente') || query.includes('réu') || query.includes('réus')) {
                response = "Seu cliente é inocente até que se prove que ele pagou suas custas em dia. Caso contrário, a inocência é apenas um detalhe. Lembre-se, um cliente satisfeito é aquele que nunca mais te procura... de dentro da prisão.";
            } else if (query.includes('indefere') || query.includes('indeferir')) {
                response = "Quem me dera ter o poder do Juiz! Mas, entre nós, o segredo é ser persistente. Ou talvez, mude o nome da sua petição para 'Pedido Urgente para o Café'. Nunca se sabe...";
            }
            else {
                response = specialistPhrases[2]; // "Essa galera do direito vive no mundo da lua. Aqui fora, a lei é outra."
            }
            specialistResponseDiv.textContent = response;
            specialistInput.value = '';
            playClickSound(); // Play sound on specialist advice
        }
        // Specialist Unlockable Resource (updated for internal functionality)
        function getSpecialistUnlockedResource() {
            const specialistResponseDiv = document.getElementById('specialistResponse');
            const randomIndex = Math.floor(Math.random() * specialistUnlockedResources.length);
            const resourceText = specialistUnlockedResources[randomIndex];
            specialistResponseDiv.textContent = resourceText;

            // Specific visual/functional effects for Specialist
            if (resourceText.includes('Chapéu de Aba Larga')) {
                const avatar = document.querySelector('.character-specialist .character-avatar');
                avatar.style.transition = 'transform 0.5s ease';
                avatar.style.transform = 'rotate(10deg)';
                const hatEmoji = document.createElement('span');
                hatEmoji.textContent = '🎩';
                hatEmoji.style.fontSize = '1em';
                hatEmoji.style.position = 'absolute';
                hatEmoji.style.top = '-10px';
                hatEmoji.style.left = '50%';
                hatEmoji.style.transform = 'translateX(-50%)';
                avatar.appendChild(hatEmoji);
                setTimeout(() => {
                    hatEmoji.remove();
                    avatar.style.transform = 'none';
                }, 3000);
            } else if (resourceText.includes('Fumaça Misteriosa')) {
                const specialistCard = document.querySelector('.character-specialist');
                const smoke = document.createElement('div');
                smoke.style.position = 'absolute';
                smoke.style.width = '100px';
                smoke.style.height = '50px';
                smoke.style.background = 'rgba(100, 100, 100, 0.5)';
                smoke.style.borderRadius = '50%';
                smoke.style.filter = 'blur(10px)';
                smoke.style.bottom = '20px';
                smoke.style.left = '50%';
                smoke.style.transform = 'translateX(-50%)';
                smoke.style.opacity = '0';
                smoke.style.transition = 'all 2s ease-out';
                specialistCard.appendChild(smoke);
                setTimeout(() => smoke.style.opacity = '1', 100);
                setTimeout(() => smoke.remove(), 2100);
            } else if (resourceText.includes('bode expiatório')) {
                const scapegoatNames = ["João Inocente", "Maria Distraída", "Pedro Azarado"];
                const randomName = scapegoatNames[Math.floor(Math.random() * scapegoatNames.length)];
                specialistResponseDiv.textContent += ` Sugestão de bode expiatório: ${randomName}`;
            } else if (resourceText.includes('Bloco de Notas Contábil')) {
                const avatar = document.querySelector('.character-specialist .character-avatar');
                const notebookEmoji = document.createElement('span');
                notebookEmoji.textContent = '📝';
                notebookEmoji.style.fontSize = '1em';
                notebookEmoji.style.position = 'absolute';
                notebookEmoji.style.bottom = '10px';
                notebookEmoji.style.right = '10px';
                avatar.appendChild(notebookEmoji);
                setTimeout(() => notebookEmoji.remove(), 3000);
            }
            playClickSound();
        }


        // Advogado da Shopee Functions
        const shopeeAdvice = [
            { query: 'frete', advice: "Nosso serviço de frete jurídico é o mais rápido, mas a entrega da sentença pode demorar, dependendo da alfândega judicial." },
            { query: 'desconto', advice: "Desconto na pena? Estamos trabalhando em um cupom 'JULGAMENTOLEVE' para a próxima remessa de réus!" },
            { query: 'compra', advice: "Para cada 'compra' de liberdade, você ganha 'shopee moedas' que podem ser trocadas por... mais liberdade? Ainda estamos negociando isso." },
            { query: 'devolução', advice: "Devolução da pena? Só se o produto (o réu) estiver intacto e na embalagem original, claro." }
        ];
        function getShopeeAdvice() {
            const shopeeInput = document.getElementById('shopeeInput');
            const shopeeResponseDiv = document.getElementById('shopeeResponse');
            const query = shopeeInput.value.toLowerCase();
            let response = shopeeAdvice.find(item => query.includes(item.query))?.advice || shopeePhrases[2]; // Fallback to a general phrase if no specific match
            
            shopeeResponseDiv.textContent = response;
            shopeeInput.value = '';
            playClickSound(); // Play sound on shopee advice
        }
        // Shopee Unlockable Resource (updated for internal functionality)
        function getShopeeUnlockedResource() {
            const shopeeResponseDiv = document.getElementById('shopeeResponse');
            const randomIndex = Math.floor(Math.random() * shopeeUnlockedResources.length);
            const resourceText = shopeeUnlockedResources[randomIndex];
            shopeeResponseDiv.textContent = resourceText;

            // Specific visual/functional effects for Shopee
            if (resourceText.includes('Botão \'Comprar Pena\' Ativado!')) {
                const shopeeCard = document.querySelector('.character-shopee');
                const buyButton = document.createElement('button');
                buyButton.textContent = '🛒 Comprar Pena';
                buyButton.className = 'btn btn-secondary';
                buyButton.style.marginTop = '15px';
                buyButton.onclick = () => showNotification('Pena comprada! (É brincadeira, né?)', 'info');
                shopeeCard.appendChild(buyButton);
                setTimeout(() => buyButton.remove(), 3000);
            } else if (resourceText.includes('Curtidas e Corações Flutuam!')) {
                const shopeeCard = document.querySelector('.character-shopee');
                for (let i = 0; i < 5; i++) {
                    const emoji = document.createElement('span');
                    emoji.textContent = i % 2 === 0 ? '❤️' : '👍';
                    emoji.style.position = 'absolute';
                    emoji.style.fontSize = `${Math.random() * 1 + 1}em`;
                    emoji.style.top = `${Math.random() * 80 + 10}%`;
                    emoji.style.left = `${Math.random() * 80 + 10}%`;
                    emoji.style.opacity = '0';
                    emoji.style.transform = `translateY(0)`;
                    emoji.style.transition = `all 1s ease-out ${i * 0.1}s`;
                    shopeeCard.appendChild(emoji);
                    setTimeout(() => {
                        emoji.style.opacity = '1';
                        emoji.style.transform = `translateY(-50px)`;
                    }, 50);
                    setTimeout(() => emoji.remove(), 1100 + i * 100);
                }
            } else if (resourceText.includes('Dinheiro Voando!')) {
                const shopeeCard = document.querySelector('.character-shopee');
                for (let i = 0; i < 5; i++) {
                    const money = document.createElement('span');
                    money.textContent = '💸';
                    money.style.position = 'absolute';
                    money.style.fontSize = '2em';
                    money.style.top = `${Math.random() * 50 + 20}%`;
                    money.style.left = `${Math.random() * 80 + 10}%`;
                    money.style.opacity = '0';
                    money.style.transition = `all 0.8s ease-in ${i * 0.1}s`;
                    shopeeCard.appendChild(money);
                    setTimeout(() => {
                        money.style.opacity = '1';
                        money.style.transform = `translateY(-30px)`;
                    }, 50);
                    setTimeout(() => money.remove(), 900 + i * 100);
                }
            } else if (resourceText.includes('Gerar QR Code para \'Desconto Jurídico\'')) {
                const shopeeCard = document.querySelector('.character-shopee');
                const qrCode = document.createElement('div');
                qrCode.style.width = '100px';
                qrCode.style.height = '100px';
                qrCode.style.background = 'white';
                qrCode.style.border = '2px solid black';
                qrCode.style.margin = '10px auto';
                qrCode.textContent = 'QR CODE FALSO'; // Simulate QR code
                shopeeCard.appendChild(qrCode);
                setTimeout(() => qrCode.remove(), 3000);
            }
            playClickSound();
        }


        // Judge Verdict Functions (Always Denied)
        const judgeDenialResponses = [
            "Indeferido! E não tente de novo. Minha paciência tem limites... e a sua também deveria ter.",
            "Pedido indeferido. A corte não está impressionada com sua criatividade. Tente novamente em 200 anos.",
            "Indeferido! Próximo! Tenho um almoço com a balança da justiça e ela não espera.",
            "Absolutamente indeferido! Eu já vi petições mais convincentes escritas por um gato no teclado.",
            "Negado! E com um toque de desdém. Aprenda a arte da derrota elegante.",
            "Indeferido. A lei é clara. A sua interpretação, nem tanto."
        ];
        let lastJudgeResponseIndex = -1;

        function getJudgeVerdict() {
            const judgeInput = document.getElementById('judgeInput');
            const judgeResponseDiv = document.getElementById('judgeResponse');
            
            let randomIndex;
            do {
                randomIndex = Math.floor(Math.random() * judgeDenialResponses.length);
            } while (randomIndex === lastJudgeResponseIndex && judgeDenialResponses.length > 1);
            
            judgeResponseDiv.textContent = judgeDenialResponses[randomIndex];
            lastJudgeResponseIndex = randomIndex;
            judgeInput.value = '';
            playClickSound(); // Play sound on judge verdict
        }
        // Judge Unlockable Resource (updated for internal functionality)
        function getJudgeUnlockedResource() {
            const judgeResponseDiv = document.getElementById('judgeResponse');
            const randomIndex = Math.floor(Math.random() * judgeUnlockedResources.length);
            const resourceText = judgeUnlockedResources[randomIndex];
            judgeResponseDiv.textContent = resourceText;

            // Specific visual/functional effects for Judge
            if (resourceText.includes('Limpa respostas dos outros personagens!')) {
                document.getElementById('internResponse').textContent = '';
                document.getElementById('specialistResponse').textContent = '';
                document.getElementById('shopeeResponse').textContent = '';
                document.getElementById('promotorResponse').textContent = '';
                showNotification('Respostas dos outros personagens limpas pelo Juiz!', 'info');
            } else if (resourceText.includes('Ativa \'Modo Alfabeto ao Contrário\'!')) {
                judgeResponseDiv.textContent += '\nZ Y X W V U T S R Q P O N M L K J I H G F E D C B A';
            } else if (resourceText.includes('Esconde campos de input de texto dos outros personagens!')) {
                document.querySelectorAll('.character-input-area textarea').forEach(textarea => {
                    textarea.style.display = 'none';
                });
                document.querySelectorAll('.character-input-area button').forEach(button => {
                    button.style.display = 'none';
                });
                showNotification('Campos de input dos outros personagens escondidos!', 'info');
                setTimeout(() => {
                    document.querySelectorAll('.character-input-area textarea').forEach(textarea => {
                        textarea.style.display = 'block';
                    });
                    document.querySelectorAll('.character-input-area button').forEach(button => {
                        button.style.display = 'block';
                    });
                }, 5000); // Revert after 5 seconds
            } else if (resourceText.includes('Exibe o clima atual e uma \'sentença\' baseada nele!')) {
                const weatherOptions = ["Ensolarado ☀️", "Chuvoso 🌧️", "Nublado ☁️"];
                const randomWeather = weatherOptions[Math.floor(Math.random() * weatherOptions.length)];
                let sentence = '';
                if (randomWeather.includes('Ensolarado')) {
                    sentence = 'Inocente! O sol brilha para a justiça.';
                } else if (randomWeather.includes('Chuvoso')) {
                    sentence = 'Culpado! A lei é rigorosa como a tempestade.';
                } else {
                    sentence = 'Parcialmente Culpado! O tempo incerto reflete a dúvida.';
                }
                judgeResponseDiv.textContent += `\nClima: ${randomWeather}. Sentença: ${sentence}`;
            }
            playClickSound();
        }


        // Promotor Functions
        let lastPromotorResponseIndex = -1;
        let paymentLockTimeout = null;

        function getPromotorResponse() {
            const promotorInput = document.getElementById('promotorInput');
            const promotorResponseDiv = document.getElementById('promotorResponse');
            
            let randomIndex;
            do {
                randomIndex = Math.floor(Math.random() * promotorPhrases.length);
            } while (randomIndex === lastPromotorResponseIndex && promotorPhrases.length > 1);
            
            promotorResponseDiv.textContent = promotorPhrases[randomIndex];
            lastPromotorResponseIndex = randomIndex;
            promotorInput.value = '';
            playClickSound(); // Play sound on promotor response
        }
        // Promotor Unlockable Resource (updated for internal functionality)
        function getPromotorUnlockedResource() {
            const promotorResponseDiv = document.getElementById('promotorResponse');
            const randomIndex = Math.floor(Math.random() * promotorUnlockedResources.length);
            const resourceText = promotorUnlockedResources[randomIndex];
            promotorResponseDiv.textContent = resourceText;

            // Specific visual/functional effects for Promotor
            if (resourceText.includes('Monóculo Aparece no Avatar!')) {
                const avatar = document.querySelector('.character-promotor .character-avatar');
                const monocleEmoji = document.createElement('span');
                monocleEmoji.textContent = '🧐';
                monocleEmoji.style.fontSize = '1em';
                monocleEmoji.style.position = 'absolute';
                monocleEmoji.style.top = '15px';
                monocleEmoji.style.left = '60%';
                avatar.appendChild(monocleEmoji);
                setTimeout(() => monocleEmoji.remove(), 3000);
            } else if (resourceText.includes('gráfico de \'Integridade\' aparece e sobe!')) {
                const promotorCard = document.querySelector('.character-promotor');
                const chart = document.createElement('div');
                chart.style.width = '100%';
                chart.style.height = '50px';
                chart.style.background = 'linear-gradient(to right, rgba(0,0,0,0) 0%, var(--accent-green) 100%)';
                chart.style.marginTop = '10px';
                chart.style.opacity = '0';
                chart.style.transition = 'opacity 1s ease';
                promotorCard.appendChild(chart);
                setTimeout(() => chart.style.opacity = '1', 50);
                setTimeout(() => chart.remove(), 2000);
            } else if (resourceText.includes('Bloqueia a possibilidade de pagar os outros personagens por 5 segundos!')) {
                Object.keys(characterPayments).forEach(char => {
                    if (char !== 'promotor') { // Don't lock Promotor's own payment
                        const input = document.getElementById(`${char}Payment`);
                        const button = document.getElementById(characterPayments[char].buttonId);
                        input.disabled = true;
                        button.disabled = true;
                        if (paymentLockTimeout) clearTimeout(paymentLockTimeout); // Clear existing lock
                        paymentLockTimeout = setTimeout(() => {
                            input.disabled = false;
                            checkPayment(char); // Re-evaluate button state based on current value
                            paymentLockTimeout = null;
                        }, 5000);
                    }
                });
                showNotification('Pagamentos bloqueados pelos argumentos do Promotor!', 'error');
            }
            playClickSound();
        }


        // Theme Toggle Function
        function setTheme(themeName) {
            document.body.className = '';
            document.body.classList.add(themeName + '-theme');
            localStorage.setItem('selectedTheme', themeName);

            document.querySelectorAll('.theme-option').forEach(option => {
                option.classList.remove('selected');
                if (option.classList.contains(themeName)) {
                    option.classList.add('selected');
                }
            });
            
            renderAllTables();
            playClickSound(); // Play sound on theme change
        }

        // Navigation Sounds Functions
        function playHoverSound() {
            if (hoverSound) {
                hoverSound.currentTime = 0;
                hoverSound.play();
            }
        }

        function playClickSound() {
            if (clickSound) {
                clickSound.currentTime = 0;
                clickSound.play();
            }
        }

        function playTabClickSound() {
            if (tabClickSound) {
                tabClickSound.currentTime = 0;
                tabClickSound.play();
            }
        }

        // Character Payment Logic
        const characterPayments = {
            intern: { 
                threshold: 1000, 
                buttonId: 'internSecretButton', 
                messageId: 'internPayMessage', 
                unlockedResourceFn: getInternUnlockedResource 
            }, 
            specialist: { 
                threshold: 10000, 
                buttonId: 'specialistSecretButton', 
                messageId: 'specialistPayMessage', 
                unlockedResourceFn: getSpecialistUnlockedResource
            }, 
            shopee: { 
                threshold: 200, 
                buttonId: 'shopeeSecretButton', 
                messageId: 'shopeePayMessage', 
                unlockedResourceFn: getShopeeUnlockedResource
            }, 
            judge: { 
                threshold: 50000, 
                buttonId: 'judgeSecretButton', 
                messageId: 'judgePayMessage', 
                unlockedResourceFn: getJudgeUnlockedResource
            },
            promotor: { 
                threshold: 100000, // Promotor agora aceita R$ 100.000,00
                buttonId: 'promotorSecretButton', 
                messageId: 'promotorPayMessage', 
                unlockedResourceFn: getPromotorUnlockedResource
            } 
        };

        function checkPayment(character) {
            const paymentInput = document.getElementById(`${character}Payment`);
            const secretButton = document.getElementById(characterPayments[character].buttonId);
            const payMessage = document.getElementById(characterPayments[character].messageId);
            const amount = parseFloat(paymentInput.value);
            const threshold = characterPayments[character].threshold;

            // Enable payment input for Promotor
            if (character === 'promotor') {
                paymentInput.disabled = false;
            }

            if (amount >= threshold) {
                secretButton.disabled = false;
                payMessage.textContent = `Acesso liberado! Clique no botão para a surpresa!`;
                playClickSound(); 
            } else {
                secretButton.disabled = true;
                payMessage.textContent = `Pague mais de R$ ${threshold.toLocaleString('pt-BR')} para liberar!`;
            }
        }

        // Renamed function to reflect that it triggers a resource, not just opens a link
        function triggerSecretResource(character) {
            const charData = characterPayments[character];
            if (charData.unlockedResourceFn) {
                charData.unlockedResourceFn(); // Call the specific unlocked resource function
            }
            playClickSound(); 
        }

        window.onload = loadFromStorage;
        window.onbeforeunload = function(e) {
            if (unsavedChanges) {
                const confirmationMessage = 'Você tem alterações não salvas. Tem certeza que deseja sair?';
                (e || window.event).returnValue = confirmationMessage;
                return confirmationMessage;
            }
        };

        // Attach event listeners for sounds to dynamically added elements after rendering
        document.addEventListener('DOMContentLoaded', () => {
            // Initial setup for existing buttons
            document.querySelectorAll('.btn').forEach(button => {
                // Ensure a button does not have multiple click listeners if already added
                if (!button.dataset.hasClickListener) {
                    button.addEventListener('click', () => playClickSound());
                    button.dataset.hasClickListener = true;
                }
            });
            document.querySelectorAll('.tab').forEach(tab => {
                if (!tab.dataset.hasClickListener) {
                    tab.addEventListener('click', () => playTabClickSound());
                    tab.dataset.hasClickListener = true;
                }
            });

            // Set initial state for payment buttons and their inputs
            checkPayment('intern');
            checkPayment('specialist');
            checkPayment('shopee');
            checkPayment('judge');
            checkPayment('promotor'); // Now Promotor is also checked for payment

            // Re-assign onclick for the secret buttons to trigger the triggerSecretResource
            document.getElementById('internSecretButton').onclick = () => triggerSecretResource('intern');
            document.getElementById('specialistSecretButton').onclick = () => triggerSecretResource('specialist');
            document.getElementById('shopeeSecretButton').onclick = () => triggerSecretResource('shopee');
            document.getElementById('judgeSecretButton').onclick = () => triggerSecretResource('judge');
            document.getElementById('promotorSecretButton').onclick = () => triggerSecretResource('promotor');
        });
    </script>

</body>
</html>
