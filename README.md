{
  "dental_clinic_ai_system": {
    "name": "DentalAI Assistant",
    "version": "1.0",
    "timezone": "Europe/Madrid",
    "supported_languages": ["es", "gl", "en"],
    
    "modules": {
      "appointment_management": {
        "name": "Gestión de Citas y Pacientes",
        "enabled": true,
        "functions": {
          "automatic_scheduling": {
            "name": "Programación automática de citas",
            "description": "Sistema de reservas en tiempo real con disponibilidad dinámica",
            "endpoints": [
              "/api/appointments/schedule",
              "/api/appointments/availability"
            ],
            "parameters": {
              "real_time_availability": true,
              "booking_window_days": 90,
              "time_slots": ["09:00", "09:30", "10:00", "10:30", "11:00", "11:30", "12:00", "15:00", "15:30", "16:00", "16:30", "17:00", "17:30", "18:00"],
              "treatment_duration": {
                "consulta_general": 30,
                "limpieza": 60,
                "empaste": 45,
                "extraccion": 90,
                "endodoncia": 120
              }
            }
          },
          "automatic_reminders": {
            "name": "Recordatorios automáticos",
            "description": "Envío de recordatorios por múltiples canales",
            "endpoints": ["/api/reminders/send"],
            "channels": ["sms", "email", "whatsapp"],
            "schedule": {
              "first_reminder": "24_hours_before",
              "second_reminder": "2_hours_before",
              "confirmation_request": "48_hours_before"
            },
            "templates": {
              "sms": "Hola {patient_name}, recordamos tu cita el {date} a las {time} en {clinic_name}. Confirma respondiendo SÍ",
              "email": "template_appointment_reminder.html",
              "whatsapp": "whatsapp_reminder_template"
            }
          },
          "intelligent_rescheduling": {
            "name": "Reprogramación inteligente",
            "description": "Reagenda automática de citas canceladas",
            "endpoints": ["/api/appointments/reschedule"],
            "algorithms": {
              "priority_scoring": true,
              "patient_preference_matching": true,
              "optimal_slot_suggestion": true
            },
            "rules": {
              "auto_reschedule_window": 7,
              "max_reschedule_attempts": 3,
              "priority_factors": ["urgency", "treatment_type", "patient_loyalty"]
            }
          },
          "waiting_list": {
            "name": "Gestión de listas de espera",
            "description": "Sistema inteligente de lista de espera con notificaciones",
            "endpoints": ["/api/waitlist/add", "/api/waitlist/notify"],
            "notification_methods": ["sms", "email", "whatsapp", "phone_call"],
            "matching_criteria": ["preferred_time", "doctor", "treatment_type", "urgency_level"]
          },
          "patient_registration": {
            "name": "Registro de nuevos pacientes",
            "description": "Formularios digitales inteligentes para registro",
            "endpoints": ["/api/patients/register"],
            "forms": {
              "basic_info": ["name", "surname", "dni", "phone", "email", "address"],
              "medical_history": ["allergies", "medications", "previous_treatments", "medical_conditions"],
              "preferences": ["preferred_doctor", "preferred_schedule", "communication_method"]
            },
            "validation": {
              "required_fields": ["name", "phone", "email"],
              "data_verification": true,
              "duplicate_detection": true
            }
          }
        }
      },
      
      "customer_service": {
        "name": "Atención al Cliente 24/7",
        "enabled": true,
        "functions": {
          "conversational_chatbot": {
            "name": "Chatbot conversacional",
            "description": "Asistente virtual para consultas básicas",
            "endpoints": ["/api/chatbot/message"],
            "capabilities": {
              "natural_language_processing": true,
              "context_awareness": true,
              "escalation_to_human": true,
              "sentiment_analysis": true
            },
            "response_types": ["text", "quick_replies", "carousel", "image"]
          },
          "faq_system": {
            "name": "Respuestas a preguntas frecuentes",
            "description": "Base de conocimiento de tratamientos y procedimientos",
            "endpoints": ["/api/faq/search"],
            "categories": {
              "treatments": ["limpieza", "empastes", "endodoncia", "ortodoncia", "implantes"],
              "procedures": ["primera_visita", "anestesia", "post_operatorio"],
              "pricing": ["seguros", "financiacion", "precios_tratamientos"],
              "general": ["horarios", "ubicacion", "contacto"]
            },
            "search_methods": ["keyword_matching", "semantic_search", "category_filtering"]
          },
          "location_services": {
            "name": "Información sobre ubicación, horarios y servicios",
            "description": "Información práctica de la clínica",
            "endpoints": ["/api/info/location", "/api/info/schedule", "/api/info/services"],
            "data": {
              "address": "Calle Principal 123, A Coruña, Galicia",
              "coordinates": {"lat": 43.3623, "lng": -8.4115},
              "phone": "+34 981 123 456",
              "schedule": {
                "monday": "09:00-13:00, 15:00-19:00",
                "tuesday": "09:00-13:00, 15:00-19:00",
                "wednesday": "09:00-13:00, 15:00-19:00",
                "thursday": "09:00-13:00, 15:00-19:00",
                "friday": "09:00-13:00, 15:00-19:00",
                "saturday": "09:00-13:00",
                "sunday": "closed"
              }
            }
          },
          "initial_triage": {
            "name": "Triaje inicial",
            "description": "Evaluación automática de urgencia",
            "endpoints": ["/api/triage/evaluate"],
            "urgency_levels": {
              "emergency": {"priority": 1, "response_time": "immediate"},
              "urgent": {"priority": 2, "response_time": "same_day"},
              "routine": {"priority": 3, "response_time": "within_week"}
            },
            "criteria": {
              "emergency_keywords": ["dolor_intenso", "hinchazón", "sangrado", "trauma"],
              "symptoms_assessment": true,
              "pain_scale_evaluation": true
            }
          },
          "multilanguage_support": {
            "name": "Soporte multiidioma",
            "description": "Atención en español, gallego e inglés",
            "endpoints": ["/api/language/detect", "/api/language/translate"],
            "languages": {
              "es": {"name": "Español", "default": true},
              "gl": {"name": "Galego", "regional": true},
              "en": {"name": "English", "international": true}
            },
            "translation_methods": ["neural_translation", "template_based", "human_review"]
          }
        }
      },
      
      "clinical_management": {
        "name": "Gestión Clínica",
        "enabled": true,
        "functions": {
          "digital_medical_history": {
            "name": "Historial médico digital",
            "description": "Gestión segura de historiales médicos",
            "endpoints": ["/api/medical/history", "/api/medical/update"],
            "security": {
              "encryption": "AES-256",
              "access_control": "role_based",
              "audit_trail": true,
              "gdpr_compliant": true
            },
            "data_structure": {
              "patient_info": ["demographics", "contact", "insurance"],
              "medical_data": ["allergies", "medications", "conditions", "treatments"],
              "visit_history": ["dates", "procedures", "notes", "prescriptions"],
              "images": ["xrays", "photos", "scans"]
            }
          },
          "treatment_reminders": {
            "name": "Recordatorios de tratamientos",
            "description": "Sistema automático de seguimiento de tratamientos",
            "endpoints": ["/api/treatments/reminders"],
            "reminder_types": {
              "follow_up": {"frequency": "custom", "treatments": ["endodoncia", "implantes"]},
              "maintenance": {"frequency": "6_months", "treatments": ["limpieza", "revision"]},
              "medication": {"frequency": "daily", "duration": "custom"}
            },
            "channels": ["email", "sms", "app_notification"]
          },
          "post_treatment_followup": {
            "name": "Seguimiento post-tratamiento",
            "description": "Monitoreo automático después de procedimientos",
            "endpoints": ["/api/followup/schedule", "/api/followup/check"],
            "protocols": {
              "day_1": {"actions": ["pain_assessment", "care_instructions"]},
              "day_7": {"actions": ["healing_progress", "complications_check"]},
              "day_30": {"actions": ["treatment_success", "satisfaction_survey"]}
            },
            "assessment_methods": ["questionnaires", "photo_requests", "video_calls"]
          },
          "allergy_alerts": {
            "name": "Alertas de alergias y contraindicaciones",
            "description": "Sistema de alertas médicas automáticas",
            "endpoints": ["/api/alerts/allergy", "/api/alerts/contraindications"],
            "alert_types": {
              "drug_allergies": {"severity": "critical", "blocking": true},
              "material_allergies": {"severity": "high", "warning": true},
              "medical_conditions": {"severity": "medium", "informative": true}
            },
            "integration": ["prescription_system", "treatment_planning"]
          },
          "prescription_management": {
            "name": "Gestión de recetas y medicamentos",
            "description": "Control de prescripciones y medicamentos",
            "endpoints": ["/api/prescriptions/create", "/api/prescriptions/track"],
            "features": {
              "electronic_prescribing": true,
              "drug_interaction_checking": true,
              "dosage_calculation": true,
              "pharmacy_integration": true
            },
            "medication_database": {
              "antibiotics": ["amoxicilina", "clindamicina", "azitromicina"],
              "analgesics": ["ibuprofeno", "paracetamol", "metamizol"],
              "anesthetics": ["lidocaina", "articaina", "mepivacaina"]
            }
          }
        }
      },
      
      "communication_marketing": {
        "name": "Comunicación y Marketing",
        "enabled": true,
        "functions": {
          "newsletter_system": {
            "name": "Envío de newsletters",
            "description": "Campañas de email con consejos de salud dental",
            "endpoints": ["/api/newsletter/send", "/api/newsletter/schedule"],
            "content_types": {
              "health_tips": {"frequency": "monthly", "personalization": "age_based"},
              "seasonal_advice": {"frequency": "quarterly", "content": "preventive_care"},
              "clinic_updates": {"frequency": "as_needed", "content": "services_news"}
            },
            "segmentation": ["age_groups", "treatment_history", "preferences", "location"]
          },
          "prevention_campaigns": {
            "name": "Campañas de prevención personalizadas",
            "description": "Contenido educativo segmentado por edad",
            "endpoints": ["/api/campaigns/create", "/api/campaigns/target"],
            "age_segments": {
              "children": {"focus": ["caries_prevention", "orthodontics"], "age_range": "0-12"},
              "teenagers": {"focus": ["oral_hygiene", "sports_protection"], "age_range": "13-18"},
              "adults": {"focus": ["gum_disease", "whitening"], "age_range": "19-64"},
              "seniors": {"focus": ["dentures", "dry_mouth"], "age_range": "65+"}
            },
            "delivery_methods": ["email", "sms", "social_media", "in_app"]
          },
          "satisfaction_surveys": {
            "name": "Encuestas de satisfacción automáticas",
            "description": "Recolección automática de feedback",
            "endpoints": ["/api/surveys/send", "/api/surveys/analyze"],
            "survey_types": {
              "post_visit": {"timing": "24_hours_after", "questions": 8},
              "treatment_completion": {"timing": "1_week_after", "questions": 12},
              "annual_satisfaction": {"timing": "yearly", "questions": 20}
            },
            "metrics": ["nps", "satisfaction_score", "recommendation_likelihood"]
          },
          "targeted_promotions": {
            "name": "Promociones y ofertas segmentadas",
            "description": "Ofertas personalizadas basadas en historial",
            "endpoints": ["/api/promotions/create", "/api/promotions/target"],
            "segmentation_criteria": {
              "new_patients": {"discount": "20%", "services": ["first_visit", "cleaning"]},
              "loyal_patients": {"discount": "15%", "services": ["whitening", "cosmetic"]},
              "overdue_checkup": {"discount": "10%", "services": ["checkup", "cleaning"]}
            },
            "channels": ["email", "sms", "app_notification", "social_media"]
          },
          "dental_education": {
            "name": "Educación dental personalizada",
            "description": "Contenido educativo adaptado al paciente",
            "endpoints": ["/api/education/content", "/api/education/recommend"],
            "content_library": {
              "oral_hygiene": ["brushing_techniques", "flossing_guide", "mouthwash_use"],
              "prevention": ["diet_advice", "fluoride_benefits", "regular_checkups"],
              "treatments": ["procedure_explanations", "recovery_tips", "maintenance"]
            },
            "personalization_factors": ["age", "risk_factors", "treatment_history", "language"]
          }
        }
      },
      
      "analytics_reporting": {
        "name": "Análisis y Reporting",
        "enabled": true,
        "functions": {
          "metrics_dashboard": {
            "name": "Dashboard de métricas",
            "description": "Panel de control con KPIs principales",
            "endpoints": ["/api/dashboard/metrics", "/api/dashboard/realtime"],
            "key_metrics": {
              "occupancy_rate": {"calculation": "scheduled_slots/available_slots", "target": "85%"},
              "cancellation_rate": {"calculation": "cancelled_appointments/total_appointments", "target": "<10%"},
              "revenue": {"calculation": "completed_treatments_value", "period": "monthly"},
              "patient_satisfaction": {"calculation": "average_survey_score", "scale": "1-10"}
            },
            "visualization": ["charts", "graphs", "kpi_cards", "trend_lines"]
          },
          "pattern_analysis": {
            "name": "Análisis de patrones",
            "description": "Identificación de tendencias en citas y tratamientos",
            "endpoints": ["/api/analytics/patterns", "/api/analytics/trends"],
            "analysis_types": {
              "appointment_patterns": ["peak_hours", "seasonal_trends", "day_preferences"],
              "treatment_trends": ["popular_procedures", "success_rates", "duration_analysis"],
              "patient_behavior": ["booking_habits", "cancellation_patterns", "loyalty_metrics"]
            },
            "algorithms": ["time_series_analysis", "clustering", "regression_analysis"]
          },
          "demand_prediction": {
            "name": "Predicción de demanda",
            "description": "Optimización de horarios basada en predicciones",
            "endpoints": ["/api/predictions/demand", "/api/predictions/scheduling"],
            "prediction_models": {
              "appointment_volume": {"horizon": "30_days", "accuracy_target": "90%"},
              "treatment_demand": {"horizon": "90_days", "factors": ["seasonality", "promotions"]},
              "resource_needs": {"horizon": "7_days", "resources": ["doctors", "equipment", "rooms"]}
            },
            "optimization_outputs": ["staff_scheduling", "room_allocation", "inventory_planning"]
          },
          "kpi_tracking": {
            "name": "Seguimiento de KPIs",
            "description": "Monitoreo continuo de indicadores clave",
            "endpoints": ["/api/kpi/track", "/api/kpi/alerts"],
            "kpis": {
              "operational": ["appointment_utilization", "wait_times", "treatment_completion_rate"],
              "financial": ["revenue_per_patient", "collection_rate", "cost_per_acquisition"],
              "quality": ["patient_satisfaction", "treatment_success_rate", "referral_rate"],
              "efficiency": ["time_per_procedure", "equipment_utilization", "staff_productivity"]
            },
            "alert_thresholds": {"revenue": "monthly_target_-10%", "satisfaction": "<8.0"}
          },
          "financial_reports": {
            "name": "Reportes financieros automáticos",
            "description": "Generación automática de informes financieros",
            "endpoints": ["/api/reports/financial", "/api/reports/schedule"],
            "report_types": {
              "daily_summary": {"content": ["appointments", "revenue", "collections"], "delivery": "email"},
              "monthly_report": {"content": ["p&l", "patient_metrics", "kpis"], "delivery": "pdf"},
              "quarterly_analysis": {"content": ["trends", "forecasts", "recommendations"], "delivery": "presentation"}
            },
            "automation": {
              "generation_schedule": "automated",
              "delivery_methods": ["email", "dashboard", "api"],
              "recipients": ["admin", "manager", "owner"]
            }
          }
        }
      }
    },
    
    "system_configuration": {
      "database": {
        "type": "postgresql",
        "encryption": "AES-256",
        "backup_frequency": "daily",
        "retention_period": "7_years"
      },
      "security": {
        "authentication": "multi_factor",
        "authorization": "role_based",
        "data_protection": "gdpr_compliant",
        "audit_logging": "enabled"
      },
      "integrations": {
        "external_systems": ["dental_software", "payment_gateways", "sms_providers", "email_services"],
        "apis": ["rest", "graphql", "webhooks"],
        "real_time": "websockets"
      },
      "performance": {
        "response_time_target": "200ms",
        "uptime_target": "99.9%",
        "concurrent_users": 1000,
        "data_processing": "real_time"
      }
    }
  }
}
