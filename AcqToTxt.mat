
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% Create physiological files from AcqKnowledge
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%


% SETTING THE PATH
path = 'your path here'; %your path here

physiodir   = fullfile(path, '/SOURCE/physio');
outdir = fullfile(path, '/DERIVATIVES/physio');

base = [path 'sub-**_ses-' session '*'];

subj = dir(base); %check all matching subject for this session


addpath([path '/functions']) % load aknowledge functions
%check here https://github.com/munoztd0/fusy-octave-memories/blob/main/load_acq.m



for i=1:length(subj)

    cd (physiodir) %go to the folder

    subjO = char(subj(i).name);
    subjX =  subjO(end-3:end); %remove .mat extension
    filename = [subjX '.acq']; %add .acq extension
                    
    
    disp (['****** PARTICIPANT: ' subjX ' **** session ' session ' ****' ]);

    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    % OPEN FILE
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%

    
    physio = load_acq(filename); %load and transform acknowledge file

    data = physio.data; %or whatever the name is


    

    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
    % CREATE AND SAVE THE CHANNEL
    %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%



    cd (outdir) %go to the folder

    % save the data as a file text in the participant directory
    fid = fopen([subjX ',txt'],'wt');
    for ii = 1:length(data)
        fprintf(fid,'%g\t',data(ii));
        fprintf(fid,'\n');
    end
    fclose(fid);


end 
    
