# FIR-FILTER-DESIGN
# EXP 4 A: Design-of-FIR-Digital-Filter-using-Rectangular-Window

# AIM 1:  To perform Design-of-LOWPASS FIR-Digital-Filter-using-Rectangular-Window using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```sci
clc;
clear;
close;

M = input('Enter the Odd Filter Length = ');
Wc = input('Enter the Digital Cut off frequency = ');

alpha = (M - 1) / 2; // Center Value

for n = 1:M
    if (n == alpha + 1)
        hd(n) = Wc / %pi;
    else
        hd(n) = sin(Wc * ((n - 1) - alpha)) / (((n - 1) - alpha) * %pi);
    end
end

// Rectangular Window
for n = 1:M
    W(n) = 1;
end

// Windowing filter coefficients
h = hd .* W;

disp(h, 'Filter Coefficients are');

[hzm, fr] = frmag(h, 256);

subplot(2, 1, 1);
plot(2 * fr, hzm);
xlabel('Normalized Digital Frequency w');
ylabel('Magnitude');
title('Frequency Response of FIR LPF using Rectangular Window');

hzm_dB = 20 * log10(hzm);

subplot(2, 1, 2);
plot(2 * fr, hzm_dB);
xlabel('Normalized Digital Frequency W');
ylabel('Magnitude in dB');
title('Frequency Response of FIR LPF using Rectangular Window');
```
# OUTPUT:

<img width="354" height="394" alt="image" src="https://github.com/user-attachments/assets/c74cc877-daff-4fc6-a52f-278f74f65d16" />
<img width="610" height="470" alt="image" src="https://github.com/user-attachments/assets/6e13d628-cae8-4c51-b1cb-4aeedce854c1" />


# RESULT: 

Thus design of low pass FIR digital filter using-Rectangular-Window waveforms were plotted and output was verified.

# AIM 2: To perform DESIGN OF HIGH PASS FIR DIGITAL FILTERS using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```sci
clc; 
close; 

M = input('Enter the Odd Filter Length ='); 
Wc = input('Enter the Digital Cut off frequency ='); 
alpha = (M - 1) / 2 // Center Value 

for n = 1:M 
    if (n == alpha + 1) then
        hd(n) = 1 - Wc / %pi; 
    else 
        hd(n) = -sin(Wc * ((n - 1) - alpha)) / (((n - 1) - alpha) * %pi); 
    end 
end 

// Rectangular Window 
for n = 1:M 
    W(n) = 1; 
end //Windowing filter coefficients 

h = hd.*W; 
disp(h, 'Filter Coefficients are') 

[hzm, fr] = frmag(h, 256); 

subplot(2, 1, 1) 
plot(2 * fr, hzm) 
xlabel('Normalized Digital Frequency w'); 
ylabel('Magnitude'); 
title('Frequency Response of FIR HPF using Rectangular Window') 

hzm_dB = 20 * log10(hzm); 

subplot(2, 1, 2); 
plot(2 * fr, hzm_dB); 
xlabel('Normalized Digital Frequency W'); 
ylabel('Magnitude in dB'); 
title('Frequency Response of FIR HPF using Rectangular Window');
```
# OUTPUT: 

<img width="375" height="421" alt="image" src="https://github.com/user-attachments/assets/68f18fb5-a164-46f9-86b0-65ce15f1db47" />
<img width="610" height="460" alt="image" src="https://github.com/user-attachments/assets/8574d385-bdc6-42d0-8f0f-341a77a254d3" />


# RESULT: 
Thus design of HIGH pass FIR digital filter using-Rectangular-Window waveforms were plotted and output was verified.

# AIM 3: To perform DESIGN OF BAND PASS FIR DIGITAL FILTERS using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```sci
clc;
clear;
close;

M = input('Enter the Odd Filter Length = ');
Wc = input('Enter the Digital Cut off frequency = '); // Expects a vector [Wc1, Wc2]
Wc2 = Wc(2);
Wc1 = Wc(1);

alpha = (M - 1) / 2; // Center Value

for n = 1:M
    if (n == alpha + 1)
        hd(n) = (Wc2 - Wc1) / %pi;
    else
        hd(n) = ((sin(Wc2 * ((n - 1) - alpha))) - (sin(Wc1 * ((n - 1) - alpha)))) / (((n - 1) - alpha) * %pi);
    end
end

// Rectangular Window
for n = 1:M
    W(n) = 1;
end

// Windowing filter coefficients
h = hd .* W;

disp(h, 'Filter Coefficients are');

[hzm, fr] = frmag(h, 256);

subplot(2, 1, 1);
plot(2 * fr, hzm);
xlabel('Normalized Digital Frequency w');
ylabel('Magnitude');
title('Frequency Response of FIR BPF using Rectangular Window');

hzm_dB = 20 * log10(hzm);

subplot(2, 1, 2);
plot(2 * fr, hzm_dB);
xlabel('Normalized Digital Frequency W');
ylabel('Magnitude in dB');
title('Frequency Response of FIR BPF using Rectangular Window');
```

# OUTPUT: 

<img width="455" height="411" alt="image" src="https://github.com/user-attachments/assets/d29bfc88-5df0-4aba-8972-6b125721317c" />
<img width="610" height="460" alt="image" src="https://github.com/user-attachments/assets/0f64ca69-5e1d-4fc2-933d-815f52df1f73" />

# RESULT: 
Thus design of BAND pass FIR digital filter using-Rectangular-Window waveforms were plotted and output was verified.

# AIM 4: To perform DESIGN OF BAND STOP FIR DIGITAL FILTER using SCILAB.

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```sci
clc;
clear;
close;

M = input('Enter the Odd Filter Length = ');
Wc = input('Enter the Digital Cut off frequency = '); // Expects a vector [Wc1, Wc2]
Wc2 = Wc(2);
Wc1 = Wc(1);

alpha = (M - 1) / 2; // Center Value

for n = 1:M
    if (n == alpha + 1)
        hd(n) = 1 - ((Wc2 - Wc1) / %pi);
    else
        hd(n) = ((sin(Wc1 * ((n - 1) - alpha))) - (sin(Wc2 * ((n - 1) - alpha)))) / (((n - 1) - alpha) * %pi);
    end
end

// Rectangular Window
for n = 1:M
    W(n) = 1;
end

// Windowing filter coefficients
h = hd .* W;

disp(h, 'Filter Coefficients are');

[hzm, fr] = frmag(h, 256);

subplot(2, 1, 1);
plot(2 * fr, hzm);
xlabel('Normalized Digital Frequency w');
ylabel('Magnitude');
title('Frequency Response of FIR BSF using Rectangular Window');

hzm_dB = 20 * log10(hzm);

subplot(2, 1, 2);
plot(2 * fr, hzm_dB);
xlabel('Normalized Digital Frequency W');
ylabel('Magnitude in dB');
title('Frequency Response of FIR BSF using Rectangular Window');
```

# OUTPUT: 

<img width="441" height="470" alt="image" src="https://github.com/user-attachments/assets/380845ed-7b40-4d99-b2b9-ccd159671377" />
<img width="610" height="460" alt="image" src="https://github.com/user-attachments/assets/1adf0872-09cc-4120-a757-1a40f67dc4e2" />

# RESULT: 
Thus design of BAND STOP FIR digital filter using-Rectangular-Window waveforms were plotted and output was verified.
