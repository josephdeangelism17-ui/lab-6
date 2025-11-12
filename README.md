def angle_to_pwm(angle: float) -> int:
    # Make sure the angle is between 0 and 180 degrees
    angle = max(0, min(180, angle))
    
    # Basic servo settings
    min_pulse = 500       # Pulse width for 0 degrees
    max_pulse = 2500      # Pulse width for 180 degrees
    period = 20000        # Time for one full PWM cycle (20ms)
    max_value = 65535     # Maximum value for 16-bit PWM

    # Find the pulse width for the given angle
    pulse_range = max_pulse - min_pulse
    pulse = min_pulse + (pulse_range * (angle / 180.0))

    # Convert pulse width to PWM duty value
    duty = int((pulse / period) * max_value)
    
    return duty
