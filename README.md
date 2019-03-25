# ButtonCommand
A better [IMHO] alternative to RelayCommand in C#

So, I got fed up with always having to create a method for CanExecute, and another for the text of the button with a NotifyPropertyChanged for each and every button.

Consequently, I created this class to do all of the boiler plate, repetitive stuff for me.

Use it thus:

in XAML:

  Button x:Name="BtnExit" HorizontalAlignment="Right" Margin="0,0,10,10" VerticalAlignment="Bottom" Width="75" Height="20"
          Content="{Binding ExitCmd.Text}" Command="{Binding ExitCmd}"

In the Class that is in the DataContext for the XAML:

        public BtnCmd ExitCmd { get; set; }
        public void Exit(object obj)
        {
            Environment.Exit(0);
        }

And, finally, in the Constructor:

            ExitCmd = new BtnCmd(Exit) { Text = "E_xit" };

Much simpler than the RelayCommand, and to Dis/Enable the button:

ExitCmd.IsExecutable = false;

ExitCmd.IsExecutable = true;

ExitCmd.IsExecutable = [condition];
